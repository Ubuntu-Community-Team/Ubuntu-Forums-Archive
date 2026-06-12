---
title: "Display freezes in Ubuntu 9.10"
date: 2009-11-01
forum: Desktop Environments
---

### Post by cvrprakash on 2009-11-01
Hi All,

I am a linux user for past 1 year. I was using Ubuntu 9.04(32bit) and yesterday I updated it to Ubuntu 9.10(64bit).
From that time I am having a problem with display.
My monitor is HP 1740 TFT.
The screen freezes, key board hangs and the only way out from that is to force reboot the system.
I searched for the /etc/X11 directory and not able to locate the xorg.conf file.
I tried reshuffling the screen resolution and that too din't work and Ubuntu is not able to grab my monitor as always it says "Unknown Monitor".

user@ubuntu910X:/etc/X11$ ls -lt
total 68
lrwxrwxrwx 1 root root    13 2009-10-30 23:52 X -> /usr/bin/Xorg
drwxr-xr-x 2 root root  4096 2009-10-27 23:45 Xsession.d
-rw-r--r-- 1 root root    14 2009-10-27 23:45 default-display-manager
drwxr-xr-x 2 root root  4096 2009-10-27 23:44 cursors
drwxr-xr-x 2 root root  4096 2009-10-27 23:44 app-defaults
drwxr-xr-x 3 root root  4096 2009-10-27 23:44 xinit
drwxr-xr-x 6 root root  4096 2009-10-27 23:37 fonts
-rw------- 1 root root   601 2009-10-27 23:29 Xwrapper.config
drwxr-xr-x 2 root root  4096 2009-10-27 23:28 Xresources
drwxr-xr-x 2 root root  4096 2009-10-27 23:27 xkb
-rw-r--r-- 1 root root    13 2009-08-25 06:13 XvMCConfig
-rw-r--r-- 1 root root 17394 2009-06-23 04:27 rgb.txt
-rwxr-xr-x 1 root root  3730 2008-06-25 07:35 Xsession
-rw-r--r-- 1 root root   265 2008-06-25 07:35 Xsession.options
user@ubuntu910X:/etc/X11$

Please suggest me a fix, I don't want to move out of Ubuntu.

Thanks
Prakash R

---

### Post by billharris on 2009-12-06
Prakash, good luck.  I have no answer, but I do have a bit of data.

I've been a *nix user for quite a while, and Hardy and Intrepid were both rock-solid for me.  Jaunty was great at the start, but it started to freeze after about last May - June - July, and it got to the point that it would freeze between several times a day to once every day or two.  Only Alt-SysReq REISUB would restart it.

I did a clean install of Karmic (all 32-bit), and things are much better.  Still, I do get X to freeze every 1-3 days, it seems like.  I can kill X and recover; I could not do that in Jaunty.

I can go to a virtual terminal and kill firefox or some other application, and sometimes that gives me a bit of extra time to close other open apps before restarting X.

Virtual terminals work, but the screen is all black, so I am typing blind and can only see side-effects if they show up back in X.

If I've got the timing right of my last restart, I don't see anything unusual in the logs. 

In Jaunty, I would catch top showing 3GB of memory in use shortly before it would crash, even though the System Monitor showed much less.  I haven't checked in Karmic yet.

Ideas anyone?

---

