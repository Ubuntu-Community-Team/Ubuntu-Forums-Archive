---
title: "Cant Mount UDF Volume"
date: 2008-02-25
forum: Desktop Environments
---

### Post by dontgetshocked on 2008-02-25
Here is my fstab and I also installed all, (I Believe) the gstreamer files. Any suggestion?


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=351699c6-7930-488d-9ba8-810d59a583c4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=872728c5-729f-41f5-813a-6ec99792e134 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by SonicSteve on 2008-02-26
What kind of UDF volume are you trying to mount?

For instance, if you burn a DVD with Windows Vista you will likely not be able to view it. You'll get a mount Icon called "UDF Volume" there will be one file in it telling you about UDF volumes.

Is this the trouble you have or is it something else. We need more details.

---

### Post by slacka-vt on 2008-04-11
I am having that error now with a DVD my buddy burned with Vista.
Can we get this thread "fired up" again ?

~s

---

### Post by FuturePilot on 2008-04-11
Yes, this is a know problem with DVDs burned in Vista. Ubuntu doesn't include the new UDF 2.5.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196730]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196730")

But there's a thread here explaining how to compile it
[http://ubuntuforums.org/showthread.php?t=718744]("http://ubuntuforums.org/showthread.php?t=718744")

---

### Post by dontgetshocked on 2008-04-23
It appears that I can indeed read udf on my dvd drive, just not a cdr disk.

---

