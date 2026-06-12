---
title: "Ubuntu 11.04 Wubi"
date: 2011-04-30
forum: Desktop Environments
---

### Post by qzpac on 2011-04-30
OS: Ubuntu version 11.04 Final and Windows Server 2008 Standard
Motherboard : Gigabyte GA-H67M-D2-B3
BIOS Type/Date/Version: Award Modular v6.00PG
Processor : Intel Core i3-2100CPU - 3.10GHz
Chipset: Intel H67 chipset
Ram :  Kingston 4GB
HDD : 500Gb seagate sata

I have 2 OS: 
1. Ubuntu version 11.04 Final 
2. Windows Server 2008 Standard

installed using wubi 11.04. 

Once Windows server 2008 expired, can i use ubuntu 11.04 installed using wubi to be my operating system forever? If windows server crashes after expired, can i still use my ubuntu 11.04......

---

### Post by bcbc on 2011-04-30
Wubi is great to try out Ubuntu. But if you are planning to use it permanently you'd do better with a full dual boot install. Wubi relies on the underlying ntfs (or fat - but usually ntfs) file system and you can only fix ntfs corruption from windows (or a windows repair prompt).

---

### Post by joegeek on 2011-04-30
Don't quote me but, I'm gonna say yes.  Why not install Ubuntu in its own right?  You don't have to do a fresh install, and there by loose your current Ubuntu desktop setting, or any other works on your current Ubuntu install.  Just resize your Windows partition, create ext4 & swap partitions, and [migrate]("http://ubuntuforums.org/showthread.php?t=1519354"). (btw: thanks bcbc, migrated a Wubi install myself using your instructions from your thread.)

---

