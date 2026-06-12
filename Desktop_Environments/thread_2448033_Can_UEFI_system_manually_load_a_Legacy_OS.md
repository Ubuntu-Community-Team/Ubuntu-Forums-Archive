---
title: "Can UEFI system manually load a Legacy O/S"
date: 2020-07-31
forum: Desktop Environments
---

### Post by Geoff_Lane on 2020-07-31
Folks,

I know how to manually boot from a GRUB menu, I have a number of custom entries in /etc/grub.d/40_custom so have an idea as to what is needed to load an O/S but far from an expert :cool:

I have an older external drive that to date I have switched to legacy BIOS to use but looking at the GRUB entries they look the same or similar to a manual boot from UEFI

I did try a manual boot of the legacy system but got some message telling me the kernel was too old (Apologies, didn't note it properly) whereas it boots fine if I switch to legacy.

Geoff

---

### Post by grahammechanical on 2020-07-31
It could be that the message is simply warning that the version had reached end of its support life.

If we are dual booting on a UEFI system then we should take note of this advice

> Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 


[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

So, you may have go through a complicated ritual each time you want to boot into one or the other of the installed OS.

Regards.

---

### Post by Geoff_Lane on 2020-08-03
> **grahammechanical said:**
> It could be that the message is simply warning that the version had reached end of its support life.

If we are dual booting on a UEFI system then we should take note of this advice



[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

So, you may have go through a complicated ritual each time you want to boot into one or the other of the installed OS.

Regards.

Strange, the manual entries for both seem identical so having difficulty understanding the logic behind each.  Got an external drive with msdos partition table and six Linux O/Ss (Extended partition with logical drives) and boots fine using UEFI but older disk with 2 Ubuntu systems installed using Legacy BIOS won't.

Seldom have a need to use the old drive installed under Legacy BIOS so mere curiosity as to why same manual commands on UEFI and Legacy don't work.

Ah well, with the thousands or millions of instructions involved it is a wonder anything works :cool::cool:

Geoff

---

