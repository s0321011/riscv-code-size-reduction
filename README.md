Welcome to the RISC-V Code Size Reduction Group
------------------------------------------------

This will be the home for the all of the code size reduction proposals, analysis, results etc.

Documentation of existing ISA extensions
- [Existing ISA extensions to reduce code size](https://github.com/riscv/riscv-code-size-reduction/blob/master/existing_extensions/README.md)

ISA extension proposals
- [Push/Pop](https://github.com/riscv/riscv-code-size-reduction/blob/master/ISA%20proposals/Huawei/riscv_push_pop_extension_RV32_RV64.adoc)

Publicly available benchmarks
- [Embench](https://github.com/embench/embench-iot)

  - antecedents [BEEBS](https://github.com/mageec/beebs), [MiBench](http://vhosts.eecs.umich.edu/mibench/), [Mälardalen WCET benchmarks](https://drops.dagstuhl.de/opus/volltexte/2010/2833/pdf/15.pdf), [Hacker's Delight/A Hacker's Assistant](https://en.wikipedia.org/wiki/Hacker%27s_Delight)

- [TACLe Benchmarks](http://www.tacle.eu/)
- [softfloat](http://www.jhauser.us/arithmetic/SoftFloat.html) and [testfloat](http://www.jhauser.us/arithmetic/TestFloat.html)
- [MLPerf](https://mlperf.org/) - specifically for AI/ML applications

Proprietary benchmarks
- Huawei IoT code
- others?

Useful papers
- [Peijie Li's Berkeley paper](https://www2.eecs.berkeley.edu/Pubs/TechRpts/2019/EECS-2019-107.pdf)

Current open issues to discuss in meetings
------------------------------------------

- How to report code size, Ofer suggests total size of all read-only sections in the elf file
- Whether synopsys would be interested in letting us compare against Metaware for ARC v2, or if we should just keep it to open source (ARC v1). In general comparisons should be against open source compilers except where we have specific support, i.e. IAR
- Review of push/pop proposal and how to handle the EABI cases
  - different meaning of register lists (different X registers from s2 onwards), and how to specify them in the assembler syntax
  - different stack alignment 8 / 16-bytes
  - selecting either ABI in software for I (32-reg) architectures
  

Reference Architectures
-----------------------

These are architectures we could compare against. The "official" comparison architectures have not yet been decided, but almost certainly need freely available ISA manuals and GCC+LLVM ports

- ARMv7-M / Cortex-M3 [manual is here](https://developer.arm.com/documentation/ddi0403/ed/)
- ARCv1 / ARC700 [manual is here](http://me.bios.io/images/d/dd/ARCompactISA_ProgrammersReference.pdf) _ARCv2 would be better but is proprietary (ISA and toolchain)_
- NanoMIPs [manual is here](https://s3-eu-west-1.amazonaws.com/downloads-mips/I7200/I7200+product+launch/MIPS_nanomips32_ISA_TRM_01_01_MD01247.pdf) see "save" instruction on page 163 and "restore/restore.js" instructions on page 155
- AVR32 [manual is here](http://ww1.microchip.com/downloads/en/DeviceDoc/doc32000.pdf)
- J-core [manual is here](https://j-core.org/) a reimplementation of Hitachi SH2 
- SuperH [instruction reference is here](http://www.shared-ptr.com/sh_insns.html)

Reference Toolchains
--------------------

- ARM GCC / LLVM? Version / download link?
- [ARC](https://github.com/foss-for-synopsys-dwc-arc-processors/toolchain/releases)

Code size reduction ideas
-------------------------

Need a lot more detail for these, they're just placeholders at the moment

- runtime library optimisation
- link time optimisation including dead code elimination
- function prologue/epilogue optimisation in software, to close the gap with the PUSH/POP ISA extension proposal
- smaller instruction sequences to jump to distant addresses
- smaller instruction sequences to load/store to distant addresses
- smaller instruction sequences to load 32-bit constants
- many more I'm sure......

Experiments
-----------

- enable B-extension, maybe a subset could become part of a future code-size reduction ISA extension





