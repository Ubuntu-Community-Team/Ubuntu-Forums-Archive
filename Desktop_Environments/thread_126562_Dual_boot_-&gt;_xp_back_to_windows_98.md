---
title: "Dual boot -&gt; xp back to windows 98"
date: 2006-02-06
forum: Desktop Environments
---

### Post by jhbumby on 2006-02-06
Since there is so much controversy over the issue, I decided to install my legitimate copy of windows 98 SE.  I have ubuntu/XP dual boot now.  I tried GParted, but said

"
At least one operation was applied to a busy device.

A busy device is a device with at least one mounted partition.
Because making changes to a busy device may confuse the kernel, you are advised to reboot your computer.
"

All I want is XP off so I can install 98 SE in its place.  Thank you,
John

---

### Post by dcstar on 2006-02-06
[QUOTE=jhbumby]Since there is so much controversy over the issue, I decided to install my legitimate copy of windows 98 SE.  I have ubuntu/XP dual boot now.  I tried GParted, but said

"
At least one operation was applied to a busy device.

A busy device is a device with at least one mounted partition.
Because making changes to a busy device may confuse the kernel, you are advised to reboot your computer.
"

All I want is XP off so I can install 98 SE in its place.  Thank you,
John[/QUOTE]
sudo umount "your-xp-mounted-drive" (use "mount" to list all of your mounts)

Then you should be able to delete the XP partition (which is what I assume you are trying to do?)

---

### Post by jhbumby on 2006-02-06
Then I get this:
"
jhbumby@JB:~$ sudo umount hda1
umount: hda1: not found
jhbumby@JB:~$ sudo umount /dev/hda1
umount: /dev/hda1: not mounted
jhbumby@JB:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
"
Let me try something -> I'll be back

---

### Post by jhbumby on 2006-02-06
Okay, so I may have screwed something up big time.  The HDA1 icon on my linux destop is gone.  The swap shows both ubuntu and windows xp, but xp will not work, and error screen comes up almost immediately after clicking on windows xp.  It shows that windows is unmounted, but I can not load windows 98 yet.  wtf --- please help
John

---

### Post by jhbumby on 2006-02-07
Anyone know what's going on here???  Please help!!!!

---

### Post by plors on 2006-02-08
there's nothing going on here... It's a simple warning which gives you some advice. Since it apperantly confuses users the developers have decided to remove that warning in the next release.

---

### Post by dcstar on 2006-02-08
[QUOTE=jhbumby]Okay, so I may have screwed something up big time.  The HDA1 icon on my linux destop is gone.  The swap shows both ubuntu and windows xp, but xp will not work, and error screen comes up almost immediately after clicking on windows xp.  It shows that windows is unmounted, but I can not load windows 98 yet.  wtf --- please help
John[/QUOTE]
If your XP partition is unmounted, then you should be able to delete it (so you than then install W98 in the space).

If you don't want Linux to do it, boot up with your Win 98 install disk and delete the partition with their utilities.

---

