---
title: "Xorg server"
date: 2012-06-26
forum: Desktop Environments
---

### Post by nagarajuk on 2012-06-26
Hi ,

I am working on  ROOTFS  ,I want to intigrate Xorg server. I have copied all the Xorg related binaries and dependencies from the UBUNTU ROOTFS to my rootfs.Now Xorg server is running.In ubuntu rootfs 05-evdev.conf file is there and Xorg is using that conf and all are USB mouse ,USB keyboard and touch are working in ubunu rootfs.In my case these 05-evdev.conf files is there but my Xorg not finding the matching ones and not working with this.I have created one xorg.conf and placed in the /etc/X11/xorg.conf here i am using input device section as generic keyboard like i have created the .conf file.Here i am giving the device path like /dev/input/event8 for mouse and  /dev/input/event9 .After USB mouse and USB keyboard connecting ,if i start run Xorg & then my USB keyboard and mouse are working fine.If remove and instert it again my Xorg is not detecting the USB keyboard and mouse as hotplug.

Please help me what are all i am missing and how to dibug this issue.In UBUNTU ROOTFS it is working fine.

When i try to run Xorg i am getting the below message
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.31-607-imx51 armv7l Ubuntu
Current Operating System: Linux freescale 2.6.35.3-998-ga1cd8a7 #72 PREEMPT Wed Apr 25 11:34:01 IST 2012 armv7l
Kernel command line: console=ttymxc0,115200 console=ttymxc0 root=/dev/mmcblk0p1 rootwait rw video=mxcdi0fb:RGB24,1024x768M@60 hdmi ip=dhcp
Build Date: 23 April 2010  05:19:26PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <[EMAIL="bryce@ubuntu.com"]bryce@ubuntu.com[/EMAIL]>) 
Current version of pixman: 0.16.4
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan  1 02:22:46 1970
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"

Fatal server error:
xf86OpenConsole: Cannot open /dev/tty0 (No such file or directory)


Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

[1]+  Done(1)                 Xorg

Please suggest me how to reslove this



Thanks,
Nagaraj

---

