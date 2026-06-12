---
title: "Xp into ubuntu using Vmware, How ?? please help"
date: 2009-04-08
forum: General Help
---

### Post by kiiwii14 on 2009-04-08
Hi

i have a ubuntu, and XP OS. There are installed into the same hard disk. i want to use vmware to boot XP into the ubuntu...

my main OS is ubuntu... i want to use the **_existed_** OS, i don't want to install a new OS of XP... and i want the HDD to be shared, i don't want to allocate a new space for it...
how i do that ???

Note:
i'm kind noob with ubuntu, and i did already installed the vmware software.

Thanks in advance

---

### Post by 3Miro on 2009-04-08
I have seen howtos on how to do that with Virtual Box, however, I have no idea how VM Ware works. Does it have a manual or something, the Virtual box manual is quite easy to read.

---

### Post by 3rag0n on 2009-04-08
In VMware, or any other virtualization software for that matter, what happens is that you run a **GUEST OS (XP)** inside a **HOST OS (Ubuntu)**. 

Suppose you want to run XP via VMware in Ubuntu. 

1. Tell VMware to create a new Virtual Machine. What it does is that it creates a simulated computer. The simulated (or "virtual") computer is like another computer inside your "real" computer. 

2. It will ask you what OS you wish to run. If you say XP, it will create a machine with hardware configuration that works best with XP.

3. Unfortunately Micro$oft does NOT provide LiveCDs of Windows XP. Therefore, to use XP you must install it. To install XP, you need a hard drive. But remember, the machine is "simulated". So, a virtual Hard drive will be created. This virtual drive is a file of predefined size. For example, if you want a 10 GB hard drive, it will create a file of size 10 GB and XP will write stuff into that file.

---

### Post by 3Miro on 2009-04-08
If you already have installation of XP on a drive, you can make it wun under Virtual Box without the need to reinstall. I am not sure about VM ware, I would think it can do that, but I am not sure how.

---

### Post by kiiwii14 on 2009-04-09
> **3Miro said:**
> If you already have installation of XP on a drive, you can make it wun under Virtual Box without the need to reinstall. I am not sure about VM ware, I would think it can do that, but I am not sure how.

I also have virtualbox... how can it be done ?? i did digg in the software and i didn't get it yet... where is that function ??

Thanks in advance

---

### Post by kiiwii14 on 2009-04-09
Thank you guys, i solved the problem...

Thank you again for your efforts

---

