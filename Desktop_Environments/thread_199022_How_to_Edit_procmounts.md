---
title: "How to Edit /proc/mounts"
date: 2006-06-18
forum: Desktop Environments
---

### Post by larry on 2006-06-18
Hello,
I am having some problems to mount a USB memory stick using XFCE, but I think the problem is not XFCE-dependent. After learning something about the fstab file, I chose to add this line to manage usb memory sticks:

 /dev/sda1 /mnt/memorystick vfat user,noauto,rw 0 0 uid=1000 gid=1000

(I found out my uid and gid with "id larry").
However, this still leads to plenty of problems (mainly, I normally can mount my memory stick as a read-only device).
I typed:                    more /proc/mounts
and saw this line:

/dev/sda1 /mnt/memorystick vfat [COLOR="Red"]ro[/COLOR],nodiratime,nosuid,nodev,noexec,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 0 0

so I think the problem has to be related to the read-only permission I highlighted in red. However, how can I change it to rw? I tried to sudo nano or gedit that file, but I cannot modify it. I see that it looks like a link to something else, but I do not know enough about linux to fix this problem by myself.
Many XFCE users are reporting some problems with memory sticks, so fixing this thing could give them a hand as well.
Cheers

Larry

---

