---
title: "Strike F1!"
date: 2008-11-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by orionyoung on 2008-11-29
So a friend down the road was having trouble with his pc and asked me to look at it. It's a Dell DE051 and had XP installed. He said for weeks virus's had been building up until one day it stopped booting up! He asked to me install what I was using on his pc, so I installed Ubuntu 8.10. It went fine until I rebooted it and the following shows up...
"Strike F1 to retry boot, F2 for setup utility"
Needless to say the F1 does nothing  but repeat the phrase! Meanwhile, if I boot with the instillation CD and choose the bottom option to boot from first Hard drive, it boots with now problems!? What is going on here? Has anyone else had this problem! Thanks in advance for any help

orion

---

### Post by armandh on 2008-11-29
check the bios battery

---

### Post by orionyoung on 2008-11-29
The battery is probably fine. It keeps good time even when turned off for a couple days, but I'll check any way.

---

### Post by falcon61102 on 2008-11-29
When you performed the install did you check the box to install the GRUB boot loader?  It sounds like there are no boot files installed.

Try booting up from the LiveCD and opening a terminal: Applications>Accessories>Terminal.  Then type the following:
```
sudo grub
```

That will load the GRUB prompt.  Then type:
```
find /boot/grub/stage1
```

That will attempt to locate the boot files for Ubuntu.  You will either get an error or something that looks like: (hd0,0).

If you get an error, then it might be that the GRUB was never installed.  Your best bet at this point is to download and burn the Super GRUB disk and use that to fix the problem.  It can be found at: [www.supergrubdisk.org](www.supergrubdisk.org)

---

### Post by caljohnsmith on 2008-11-29
One thing you should probably check is if one of the partitions on the HDD is marked as bootable, because if not, some BIOSes will refuse to boot a drive that doesn't have one partition marked as bootable. You can check by booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And look for an asterisk * under the boot heading. If none of the partitions are flagged as bootable, you could do:
```
sudo grub
grub> root (hd0,0)
grub> makeactive
grub> quit
```
And that will set the boot flag on the first partition.

---

### Post by orionyoung on 2008-12-01
The Asterics is present! Here is what the Fdisk had to day:
"device   boot ... sys
 /dev/sda1  *      linux
 /dev/sda2         extended
 /dev/sda5         swap/linux"

Any other ideas?

orion

---

### Post by caljohnsmith on 2008-12-01
I would try reinstalling Grub to the MBR (Master Boot Record) to see if that fixes the problem. You can do that with:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And please post the output of the above commands. After that, reboot, and see if anything changes.

---

### Post by orionyoung on 2008-12-02
Ok, did everything you told me to do...

Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stagel_5" exists... yes
Running embed "/boot/grub/etfs_stagel_5" (hd0)...
16 sectors are embedded.
running "install /boot/grub/stage1 (hd0)(hd0)1+16 p (hd0,0) /boot/grub/stage2
done

Then I turned it off, held my breath and rebooted... and got the same old strike F1! One possibility down, many to go!

orion

---

