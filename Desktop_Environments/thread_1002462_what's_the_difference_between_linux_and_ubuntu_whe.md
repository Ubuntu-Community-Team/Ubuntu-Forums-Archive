---
title: "what's the difference between linux and ubuntu when start up my computer"
date: 2008-12-05
forum: Desktop Environments
---

### Post by brian1125 on 2008-12-05
hello, every body
I want to know ubuntu base computer startup flow.
But in the internet i just find the linux base computer startup flow.
such that:
In detail:

   1. The BIOS performs hardware-platform specific startup tasks
   2. Once the hardware is recognized and started correctly, the BIOS loads and executes the partition boot code from the designated boot device, which contains phase 1 of a Linux boot loader. Phase 1 loads phase 2 (the bulk of the boot loader code). Some loaders may use an intermediate stage to achieve this (known as phase 1.5) since modern large disks may not be fully readable without further code.
   3. The boot loader often presents the user with a menu of possible boot options. It then loads the kernel, which decompresses into memory, and sets up system functions such as essential hardware and memory paging, before calling start_kernel().
   4. start_kernel() then performs the majority of system setup (interrupts, the rest of memory management, device initialization, drivers, etc) before spawning separately, the idle process and scheduler, and the Init process (which is executed in user space).
   5. The scheduler effectively takes control of the system management, as the kernel goes dormant (idle).
   6. The Init process executes scripts as needed that set up all non-kernel services and structures in order to allow a user environment to be created, and then presents the user with a login screen.

i very want to know the detail startup flow for ubuntu base computer.

so, if you know about my issue, tell me please.

---

### Post by mhh91 on 2008-12-05
actually,ubuntu is based on the linux kernel,there's no difference here

---

### Post by tjandracom on 2008-12-05
ubuntu is linux. there are differences among distros, but generally, it's pretty much the same.

you could read these manual for information:
```
man boot
```
```
man inittab
```
```
man bootparam
```
```
man init
```
```
man runlevel
```

---

