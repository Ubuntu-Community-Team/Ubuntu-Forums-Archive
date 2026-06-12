---
title: "avida: segmentation fault"
date: 2008-04-15
forum: Education &amp; Science
---

### Post by eb207 on 2008-04-15
I'm trying to run avida on gutsy gibbon on an amd64, and I'm getting a segmentation fault.

I copied the configuration files out of /usr/share/avida/ into a folder in my home directory, and run avida-viewer, getting the following output. Any ideas?



Instruction Library has 4 instructions.
<cHardware4Stack::initInstLib> debug: important post-init values:
 --- GetSize(): 36
 --- GetNumNops(): 4
 --- GetName(last): Inject

<cHardwareCPU::initInstLib> Instruction Library has 3 instructions.
<cHardwareCPU::initInstLib> debug: important post-init values:
 --- GetSize(): 181
 --- GetNumNops(): 3
 --- GetName(last): skip

Avida version 2.0b7
Copyright (C) 1993-2003 California Institute of Technology.

Avida comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions. See file COPYING for details.

Random Seed: 0 -> 82931882
ENV: Loading file 'environment.cfg'.
ENV: Loading reaction 'NOT' with trigger 'not'.
ENV: Loading reaction 'NAND' with trigger 'nand'.
ENV: Loading reaction 'AND' with trigger 'and'.
ENV: Loading reaction 'ORN' with trigger 'orn'.
ENV: Loading reaction 'OR' with trigger 'or'.
ENV: Loading reaction 'ANDN' with trigger 'andn'.
ENV: Loading reaction 'NOR' with trigger 'nor'.
ENV: Loading reaction 'XOR' with trigger 'xor'.
ENV: Loading reaction 'EQU' with trigger 'equ'.
Loaded Instruction Library "inst_set.default" with 26 instructions.
Initializing Population...<cPopulation>
Building world 100x100 = 10000 organisms.
Geometry: Torus
...Building Integrated Time Slicer...
Segmentation fault (core dumped)

---

