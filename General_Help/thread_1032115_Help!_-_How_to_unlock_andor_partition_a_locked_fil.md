---
title: "Help! - How to unlock and/or partition a locked file system...?"
date: 2009-01-06
forum: General Help
---

### Post by AlexsAntidote on 2009-01-06
Hello!

I tried to follow a tutorial (found here: [http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/]("http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/")) to setup a bootable and persistent Ubuntu 8.10

I kind of cheated a little bit and tried to do it on an SD card. I have a USB SD card reader that I use all the time and an extra 2GB card, I thought I'd give it a shot.

Well I followed the tutorial on my computer at work (which is an older Pentium III with Windows XP, not that it should matter).

Everything Looked OK at first, but when I tried to reboot and test it out it would not boot. I took it home and looked at it. Both Ubuntu and XP could not partition/format the drive... Both gave me some type of a "locked" warning. (although XP let me delete some files anyway).

I checked the disk to ensure it was not physically locked, which it was not.

I looked closer at the files, and while the main directory everything had regular file names, inside the subdirectories everything was corrupt!


I would really like to format and/or repartition this disk and start over.

Please help!

**Edit Below**
I wanted to add that I already checked mount in the terminal and got the following:

/dev/mmcblk0p1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

which seems to me that it is mounted with write access.
**end edit**

---

### Post by AlexsAntidote on 2009-01-06
How come every time I post a thread I end up finding the answer on my own within minutes?

I spent about 3 hours messing around trying to fix this... Searching forums, google, asking friends, and nothing. I post my question here and bam I find the answer!

In case anyone else wants to know, here's what I found that worked: [See Post # 7]("http://www.mobileread.com/forums/showthread.php?t=9062")

So I used the following commands:

```

umount /dev/mmcblk0p1
mkdosfs -F 16 -n "MyDisk" -v /dev/mmcblk0p1

```

Now I'll try the tutorial again but with some modifications... (I'm a glutton for punishment I guess).

---

