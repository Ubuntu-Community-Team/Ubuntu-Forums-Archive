---
title: "Dual Hard Drives Uninstall Ubuntu"
date: 2009-03-24
forum: General Help
---

### Post by Sideoutdude16 on 2009-03-24
How do i uninstall Ubuntu without hurting the Vista OS hard drive? I just wanted to remove ubuntu on this system since i purchased a netbook that ill be using the linux on the laptop. The question is, do i uninstall it from disk mgmnt to remove the partition but im afraid that it might mess up the boot file for Vista and the grub loader. Is there any way i can do this without touching Vista's files to remove the 2nd hard drive files and format it to a new hard drive for my backup's

---

### Post by ibuclaw on 2009-03-24
Boot from your Vista DVD Disk, and go into "**Repair Options**"->"**Command Prompt**":

Then type in the following:
```

bootrec.exe /fixmbr
bootrec.exe /fixboot
bootrec.exe /rebuildbcd 

```

Then boot into the Ubuntu LiveCD and go into "**System**"->"**Administration**"->"**Partition Manager**":
Then remove your old Linux partition. You can also resize the NTFS partition to fill the disk again, but I think Vista can do that itself (it would also be better to do it from Vista if possible).

Regards
Iain

---

### Post by Sideoutdude16 on 2009-03-26
when i ran the vista dvd, after the windows drivers were done loading then the blue screen shows up giving me errors. so im not able to get thru the vista set up. i even disconnected the hard drive to try reading one hard drive but was not successful. So i need help big time :-D

blue screen shows

acpi.sys - address 8075a276 base at 807420000 datestamp 4549adb7

stop: 0x0000007e (oxc0000005, 0x8075a276 0x8105d5ec 0x8105d2e8

---

### Post by jocheem67 on 2009-03-26
You're using two drives?

First is vista and second is /was ubuntu?

What do you mean by errors when loading vista's cd?

Tinivole's reply seams to be the correct one.

It's all about getting the vista drive to be the boot drive and telling vista that the MBR is there to use again...

---

### Post by Sideoutdude16 on 2009-03-26
how do i go pass thru the blue screen error?

correct i am using 2 drives. one for vista then one for ubuntu. i wanted to run the repair options but its not accessible due to the blue screen error after loading the dvd.

im gonna try removing 3gb ram leaving 1gb ram in the system to see if it goes thru.

scratch my comments, it went thru! i went thru the same thing when i first installed my pc long time ago.

---

### Post by Sideoutdude16 on 2009-03-26
we can close this post. it has been successful!

---

