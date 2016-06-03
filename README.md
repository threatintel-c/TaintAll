# TaintAll
TaintAll, a taint analysis and concolic execution tool.

# Installation
- Install boost >= 1.5
- Install pin >= 2.14
- cd your_pin_path/source/tools
- git clone https://github.com/onura/TaintAll.git
- cd TaintAll
- ./compile.sh
- open ida-plugin/ta_plugin.py and set CONF_PIN_PATH variable to point your pin directory 
- cp ta_plugin.py into IDA Pro plugin directory.


# Usage
- init plugin
t = ta_plugin()
t.run(1)

- start tainting at the address
t.a.startTaintAt(0x100000EB0)

- stop tainting at the address
t.a.stopTaintAt(0x100000F41)

- taint 5 bytes from the address that RSI register is pointing to
t.a.taintPointer(0x100000F17, Registers.RSI, 5)

- taint EAX registers
t.a.taintRegister(0x100000BBC, Registers.RAX, RegParts.DWORD)

- taint 4 bytes from the memory 0x100000992
t.a.taintAddress(0x100000BBC, 0x100000992, 4)

- start analysis
t.a.startDynamicAnalysis()

- show/hide taints
t.a.hideTaints()
t.a.showTaints()

- print tainted registers/memories at the address which the cursor is pointing
t.a.printRegsEA()
t.a.printMemsEA()

- print all affected addresses
t.a.printAffectedAddrs()
