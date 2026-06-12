---
title: "Video file names end with &quot;(invalid encoding)&quot;, how to defautly mount in UTF8?"
date: 2011-04-04
forum: Desktop Environments
---

### Post by jiapei100 on 2011-04-04
Hi, all:

I'm using Ubuntu 10.10, filesystem ext4 .

My external hard drive is automatically mount in the following manner.
> /dev/sdb1 /media/usb0 ext4 rw,noexec,nodev,sync,noatime,nodiratime,commit=0 0 0

However, I've some video files on /media/usb0. Those names can't be shown correctly, with (invalid encoding) at the end of the file names. I checked
[http://ubuntuforums.org/showthread.php?t=1239904](http://ubuntuforums.org/showthread.php?t=1239904)
[http://ubuntuforums.org/showthread.php?t=124371](http://ubuntuforums.org/showthread.php?t=124371)
, it looks like I need to specify "nls=utf8" when mounting /media/usb0. But "nls=utf8" seems to be automatically absent again if I reboot my computer.

What should I do?

Rgds
JIA

---

