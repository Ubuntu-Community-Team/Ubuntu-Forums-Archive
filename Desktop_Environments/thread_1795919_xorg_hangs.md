---
title: "xorg hangs"
date: 2011-07-03
forum: Desktop Environments
---

### Post by mario.almeida on 2011-07-03
Dear All,

I have HP Elite 7200 MT Business PC (Desktop PC) with ubuntu 10.10 32bit. tried with ubuntu 11.04 but same problem. xorg hangs, only way is to do a hard reboot or ssh and kill xorg.

CPU: Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
RAM: 4GB

Tried even with latest ubuntu kernel but no solution.

Display is not properly set, I have put 

> xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode VGA1 1440x900_60.00
xrandr --output VGA1 --mode 1440x900_60.00
in /etc/gdm/Init/Default

When xorg hangs I get the below error message in Xorg.log file.

EQ overflowing. The server is probably stuck in an infinite loop.

Any idea how to solve this issue.

---

### Post by james_fried on 2011-09-03
Hi Mario,

Did you make any progress with this? It sounds like my system is in a similar situation to the one you reported.

I'm also looking at:

[http://ubuntuforums.org/showthread.php?t=1748460&highlight=EQ+overflowing&page=3](http://ubuntuforums.org/showthread.php?t=1748460&highlight=EQ+overflowing&page=3)

and

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/276518](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/276518)

Cheers,

James

---

