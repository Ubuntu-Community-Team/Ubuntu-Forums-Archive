---
title: "Kernel update and multiple boots"
date: 2006-06-15
forum: Desktop Environments
---

### Post by Steven_B on 2006-06-15
I have two seperate ubuntu boots, so I can have a stable one and one to mess with.  The primary boot is on /dev/hda4, and the secondary on /dev/hda6.  After I did the kernel update today, to 2.6.15-25-386, the new kernel won't boot properly.  It appears to die at the "mounting filesystems" right after the boot splash pops up.  How do I fix this, and make it so doesn't keep happening?
Thanks!

---

### Post by [S|G] on 2006-06-15
Can you boot in recover mode? You might try it and post any error messages that might show up.

---

### Post by Steven_B on 2006-06-15
If I wrote it down correctly, the last few lines are:
```
Attempt to access beyond end of device
hda2: rw=16, want=8, limit=2
Kernel panic - not syncing: I/O error reading memory image
```
I had this problem before when I first installed the second boot, and I got it fixed by copying the new /boot files to the original /boot.
hda2 is an extended partition, which contains hda6.

---

### Post by glotz on 2006-06-15
And is the 386 kernel really for you, that is, are you on an older processor? See [http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

---

### Post by [S|G] on 2006-06-15
This message looks like a lot a problem I had a while ago: [http://ubuntuforums.org/showthread.php?t=190256](http://ubuntuforums.org/showthread.php?t=190256)

It happened that my partitions had moved after a windows install and I had to adjust my /etc/fstab to the new values. If you have a live-cd, boot into it and from a terminal use fdisk -l to determine whether the partitions are correct. 

Then mount your hard drive (sudo mount /dev/hdaX /somepath , assuming your hard disk is had, X is your root partition number and /somepath is substituted with a directory you choose) and take a look at where your root is being mounted. If it doesn't match your fdisk -l, just correct the numer and try to boot again

---

### Post by Steven_B on 2006-06-15
> And is the 386 kernel really for you, that is, are you on an older processor? I have a new processor, but the K7 kernel has the same problem.
The root partition is correct.  I am able to boot my older kernel from this partition without any problems.
Do I need to do something special to tell the kernel to look at extended partitions?

---

### Post by Steven_B on 2006-06-16
I was able to boot the with the 2.6.15-25-K7 kernel by copying the initrd.img-2.6.15-25-k7 file from the new boot to the original one.  All of the other files in /boot were exactly the same.  While this works, I assume it will break the next time I try to update the kernel.  I am also unable to mount my logical partitions, which are the new ones.  It says:
error: device /dev/hda6 is not removable

error: could not execute pmount

---

### Post by Steven_B on 2006-06-23
Am I missing a kernel module or something to be able to read extended partitions?

---

### Post by glotz on 2006-06-25
No, the problem is **p**mount. That's trying to mount as regular user. I guess they can only mount removable drives (as suggested by the error). Try 

[B]sudo mkdir /media/name
sudo mount /dev/hda6 /media/name
[/B]
now you should be able to access it via /media/name
or use /etc/fstab to mount it automatically at start.

---

### Post by Steven_B on 2006-06-26
I can mount the partitions as root, and then I can view the with nautilus.  So, I guess this does not have to do with the kernel panic.
Somehow, copying the kernel from the second boot solves the problem, so there must be some difference in the way the kernel is being set up.  The GRUB menu entries are correct, and basically the same.

---

### Post by Steven_B on 2006-07-26
Another thing I remembered is that remembered is that the CD installed dapper kernel included the first few seconds of the splash screen, while the "upgraded to dapper" kernel did not.  Is there a way to set up the old kernel like the CD one is?  Is it something like
```
dpkg -reconfigure linux-image-2.6.15-26-k7
```?

---

### Post by Steven_B on 2007-05-04
If I recall correctly, the kernel panic occured because the kernel didn't know where to find the swap partition.  I had to add "resume=/dev/hda4" to the end of the kernel line in /boot/grub/menu.lst:
```
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda5 ro noapic nolapic quiet splash resume=/dev/hda4

```

---

