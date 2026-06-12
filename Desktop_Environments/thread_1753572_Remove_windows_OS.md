---
title: "Remove windows OS"
date: 2011-05-09
forum: Desktop Environments
---

### Post by qzpac on 2011-05-09
[SIZE=2]OS: Ubuntu version 11.04 Final and Windows Server 2008 Standard
Motherboard : Gigabyte GA-H67M-D2-B3
BIOS Type/Date/Version: Award Modular v6.00PG
Processor : Intel Core i3-2100CPU - 3.10GHz
Chipset: Intel H67 chipset
Ram :  Kingston 4GB
HDD : 500Gb seagate sata

I have 2 OS: [/SIZE] [SIZE=2]
1. Ubuntu version 11.04 Final 
2. Windows Server 2008 Standard

installed using wubi 11.04.

How can i remove Windows Server OS without formatting my hard disk data away and use the ubuntu 11.04 install using wubi instead?


[/SIZE]

---

### Post by SecretCode on 2011-05-09
It's not possible. When you use wubi to install, the entire Ubuntu OS is installed inside the Windows file system. If you uninstall Windows you will lose Ubuntu.

The best thing is to do a fresh install of Ubuntu without using wubi. Either replacing it completely, or - more safely - in a new partition so you could keep your current OSes available until you have migrated. But making space for a new partition is a bit complicated.

Why do you want to get rid of Windows completely? You could just keep it "in case" but never boot into it.

---

### Post by coffeecat on 2011-05-09
@OP, actually what you want to achieve is possible, but you do have to do some re-partitioning first, so SecretCode is correct in saying you can't remove Windows without reformatting. Depending on what your present partition setup is like, you would probably need to shrink your Windows C: partition, create Linux partitions and then do the wubi to partition migration. This is not something I have done myself, but see here:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?")

Which links to here:

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

That has merit if you have a heavily personalised and customised Ubuntu installation and you don't want to go through all the configuration again, but if yours is a fairly new installation, I would suggest that a fresh install would be quicker and easier.

Good luck!

---

