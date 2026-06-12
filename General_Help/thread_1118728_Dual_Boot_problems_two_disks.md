---
title: "Dual Boot problems two disks"
date: 2009-04-07
forum: General Help
---

### Post by whazooo on 2009-04-07
Hello
I have two 750gig hd's and I dual boot one hd for ubuntu one for xp

I need to reinstall xp, and dont know the proceedure for doing this 
with out messing up grub


ubuntu is on hd1,0 as is grub stage 1 in the /boot partion

windose is on hd0,0

I thought I could just unplug the ubuntu drive redo the windows and then just reboot but I guess not

if I unplug the the ubuntu drive and reboot I get no operating system error

and when I unplug window I get this

grub loading stage 1.5
grub loading, please wait...
error 21

any help with this would be greatly appreciated.

---

### Post by 3Miro on 2009-04-07
Option 1: boot from the live CD and edit the grub menu list file.  For a complicated HD setting, it will be tricky. I don't think I can help much other than:

```

sudo /media/disk_whatever/boot/grub/menu.lst

```

Option 2: boot from the Live CD and reinstall GRUB. It should automatically find all the OS you may have installed.

---

