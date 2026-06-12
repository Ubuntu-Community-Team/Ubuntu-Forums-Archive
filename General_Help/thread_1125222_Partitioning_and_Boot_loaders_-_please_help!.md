---
title: "Partitioning and Boot loaders - please help!"
date: 2009-04-14
forum: General Help
---

### Post by daniel014 on 2009-04-14
I have an MSI Wind netbook with a FAT recovery partition at the start of the drive which seems to be causing the problem.

I want to remove Ubuntu 8.10 so that I can install a fresh 9.04 when it is released. Like I've done before, I boot Win XP and run MbrFix in command prompt:

```
MbrFix /drive 0 fixmbr
```

except this time, instead of causing the system to boot straight to XP, the MBR goes to the MSI recovery partition. The only way to get Windows booting normally again is install Ubuntu so that GRUB finds my Windows partition.

So I need to find a way of restoring my MBR that boots the 2nd partition (Windows XP) instead of recovery.

Thank you for any help.

---

### Post by Monotoko on 2009-04-14
If want to restore Windows Bootloader and for some reason cannot use the windows installation cd, there is a simple way to do it:

NOTE: make sure you have internet working.

1) Boot with Ubuntu Live CD
2) On the terminal:

sudo apt-get install ms-sys

then

ms-sys --mbr /dev/hdX

NOTE: in my case the main windows xp system is located in hda1 so I used ms-sys --mbr /dev/hda

3) Reboot. 

That should work

---

### Post by daniel014 on 2009-04-14
Ok, I've used ms-sys before, however the partitions of my HDD seem to be labelled as sdaX (instead of hdaX)

I ran the ms-sys command in the terminal:

```
ubuntu@ubuntu:~$ sudo ms-sys --mbr /dev/sda2
/dev/sda2 seems to be a disk partition device,
use the switch -f to force writing of a master boot record

```

I then used "switch -f" and it said the MBR had been written. However, GRUB was all I got at boot up.

---

### Post by daniel014 on 2009-04-16
Bump

---

### Post by daniel014 on 2009-04-17
bump

---

### Post by ronparent on 2009-04-17
Code:

ubuntu@ubuntu:~$ sudo ms-sys --mbr /dev/sda2
/dev/sda2 seems to be a disk partition device,
use the switch -f to force writing of a master boot record

I am unfamiliar with the sysntax for ms-sys. However your code above suggests that you wrote a mbr to sda2. The mbr should be written to sda. In summation, what you are trying to accomplish is to rewrite the mbr on sda to point to sda2 where the windows boot instruction are.

---

### Post by daniel014 on 2009-04-18
I sort of understand what you're saying.

In the above post, I was told by Monotoko to do

```
sudo apt-get install ms-sys
```

then

```
ms-sys --mbr /dev/hdX
```

Which therefore would write the MBR to sda2, whereas I needed to use that command to write the MBR to sda?

So I **should** type

```
ms-sys --mbr /dev/sda
```

I think that's right, and thanks for your help.

---

### Post by daniel014 on 2009-04-18
I ran

```
ms-sys --mbr /dev/sda
```

it still boots my recovery partition :(.

This isn't such a big problem because it always works fine when Ubuntu is on with GRUB, I just wanted to know how to put it back to just Windows, especially as I have always been able to do that easily.

Thanks anyway for your help, I suppose using the MSI recovery discs will fix it.

Back to fix GRUB, can't wait for Jaunty :) ...

---

