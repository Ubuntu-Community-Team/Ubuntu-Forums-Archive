---
title: "Desktop Effects not working on nvidia CUDA 260.19.26 drivers"
date: 2011-02-17
forum: Desktop Environments
---

### Post by D3ATH-D3AL3R on 2011-02-17
I am unable to enable desktop effects on ubuntu 10.04 32bit desktop , after installing Nvidia developer drivers 260.19.26. The output is shown below:

1)nvcc -V
   nvcc: NVIDIA (R) Cuda compiler driver
   Copyright (c) 2005-2010 NVIDIA Corporation
   Built on Wed_Nov__3_16:14:08_PDT_2010
   Cuda compilation tools, release 3.2, V0.2.1221

2)cat /proc/driver/nvidia/version
   NVRM version: NVIDIA UNIX x86 Kernel Module  260.19.26  Sun Nov 28 22:38:24 PST 2010
   GCC version:  gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)

Moreover I am unable to run other code samples in "nvidia GPU computing SDK" excepts deviceQuery.
Here is the output of deviceQuery:
./deviceQuery Starting...

 CUDA Device Query (Runtime API) version (CUDART static linking)

There is 1 device supporting CUDA

Device 0: "GeForce 8400 GS"
  CUDA Driver Version:                           3.20
  CUDA Runtime Version:                          3.20
  CUDA Capability Major/Minor version number:    1.1
  Total amount of global memory:                 536150016 bytes
  Multiprocessors x Cores/MP = Cores:            1 (MP) x 8 (Cores/MP) = 8 (Cores)
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       16384 bytes
  Total number of registers available per block: 8192
  Warp size:                                     32
  Maximum number of threads per block:           512
  Maximum sizes of each dimension of a block:    512 x 512 x 64
  Maximum sizes of each dimension of a grid:     65535 x 65535 x 1
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             256 bytes
  Clock rate:                                    1.40 GHz
  Concurrent copy and execution:                 No
  Run time limit on kernels:                     Yes
  Integrated:                                    No
  Support host page-locked memory mapping:       Yes
  Compute mode:                                  Default (multiple host threads can use this device simultaneously)
  Concurrent kernel execution:                   No
  Device has ECC support enabled:                No
  Device is using TCC driver mode:               No

deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 3.20, CUDA Runtime Version = 3.20, NumDevs = 1, Device = GeForce 8400 GS


PASSED

Press <Enter> to Quit...
-----------------------------------------------------------

---

### Post by Frogs Hair on 2011-02-17
Using the same card with the Nvidia current 260.19 .06 and Compiz ccsm successfully. Is there anything in the driver release notes offer any clues ?

The 8400GS is a main stream entry level card are there any direct benefits to using those drivers ?

---

