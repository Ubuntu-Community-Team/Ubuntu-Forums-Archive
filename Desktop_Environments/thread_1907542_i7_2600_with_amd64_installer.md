---
title: "i7 2600 with amd64 installer"
date: 2012-01-11
forum: Desktop Environments
---

### Post by Learath2 on 2012-01-11
I've just installed a new hard drive for my ubuntu as i will be dual-booting my computer with windows 7. I've done dual booting before but this time something is weird the installer starts the purple ubuntu screen shows up btw downloaded 10.04 LTS just that i don't like the new desktop on 11.0 . After the purple screen nothing happens it just hangs in a black screen cd is spinning like crazy and nothing is happening. I burnt the iso on a mac dunno if that effects anything. 

Detailed info on hardware and installation objectives
```
i7 2600 not k, 8 GB Ram,  1,5 TB of hard drive space on 3 drives each 500 GB.
1 drive backup 1 drive windows. 
A fully empty 500 GB will be splitted to 250 GB partitions one for ubuntu one for random stuff.

```

---

### Post by Learath2 on 2012-01-12
Bump ??  I need help

---

### Post by howefield on 2012-01-12
Just a suggestion, might be better to install something more recent and change the desktop environment, or use another flavour altogether.

If you want to stick with 10.04, have you done the basic checks with MD5SUM to ensure you have a good download ?


[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by oldfred on 2012-01-12
+1 on howefield suggestion for a newer version. The newer kernels have updates for the newer systems. Even then I have seen that you have to add boot parameters to get system to work.

Also very new systems like your also are UEFI systems that also revert to BIOS if no efi boot partition is found and is not gpt partitioned. Is your system UEFI or BIOS booting now? If the Ubuntu installer sees a empty drive over some size it auto converts from MBR(msdos) to gpt. Windows will only boot with gpt if your are in UEFI mode.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

General info on UEFI:
[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)
Microsoft reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by Learath2 on 2012-01-14
Uh i suppose its BIOS. But i am downloading 11.0 to see if it works any better. A bit confused :). 

Edit: Checked MD5 sums.

---

