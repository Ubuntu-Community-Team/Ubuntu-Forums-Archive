---
title: "[SOLVED] Dual Boot with seperate IDE drives"
date: 2007-08-29
forum: Dell  Ubuntu Support
---

### Post by Radioman991 on 2007-08-29
Hello all:

Noob here.  I have a Dell B110 desktop.  I have 2 drives in the machine.  I have searched and tried everything to set up dual boot to XP and Linux.

I get an error from the NTLDR that gripes that the HAL.DLL is missing or corrupt if I try to boot to Linux.  XP boots fine.

Open the chassis, and pull the power from the XP drive, and Ubuntu boots like a champ!  I have even tried changing the cable configurations...currently, XP drive on Primary, drive 0  CD-ROM on secondary, drive 0 and Linux drive on Secondary drive 1.  Cableing makes it tough to put the Linux drive on Secondary Master.

When I DO put it on secondary master, Dell BIOS sees it as an onknown device.

I KNOW Ubuntu is there and works, but I cannot get past the HAL.DLL to save my life.  Any and all coments welcome

Regards, PK

---

### Post by logos34 on 2007-08-29
here's a link on dual drive dual booting you want to check out:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=confused57](http://ubuntuforums.org/showthread.php?t=179902&highlight=confused57)

You really should be using Grub on the linux drive to boot windows and not ntldr.  In which case you'll be [chainloading windows on a non-first hard disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

Remember to change the jumper when you move a hard diskfrom slave to master position or vice-versa (unless you have it set for 'cable select').

---

### Post by Radioman991 on 2007-08-31
Thanks.  Will check the links.  The hhd's should be cable select already, but will have to check when I get home...got sent out on the road for an install Labor Day weekend  GRRRR :-)

---

### Post by Radioman991 on 2007-09-10
SWEET!  Thanks for the assist.  Dual boot working fine with the info you provided.  I do have an issue with the system time, which I will detail in another post.  Thanks,

PK

---

