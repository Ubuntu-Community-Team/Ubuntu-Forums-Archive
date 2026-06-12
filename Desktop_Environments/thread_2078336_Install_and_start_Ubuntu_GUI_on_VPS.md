---
title: "Install and start Ubuntu GUI on VPS"
date: 2012-10-30
forum: Desktop Environments
---

### Post by eddied316 on 2012-10-30
Hello!

I've purchased a VPS and Installed Ubuntu.

Here's what I've done:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop

The last VPS I had all I had to do after this art is type: startx, and the GUI would load. 

I don't know what I'm doing wrong on this one. I need some help getting the GUI loaded. I'm really not that great with the commands and things and a GUI is what I really need. T

Thanks in advance

---

### Post by snowpine on 2012-10-30
Welcome to the forums!

Here are easy instructions to administer your Ubuntu Server using terminal commands and *without* installing a GUI: [https://help.ubuntu.com/12.04/serverguide/](https://help.ubuntu.com/12.04/serverguide/)

Posting the link it the hope it helps other readers who might stumble upon this thread someday. :)

---

### Post by eddied316 on 2012-10-30
It seems as though it's already been installed. Everything seemed to go through just fine. I just don't know how to get access to the GUI or start it. 

Like I said, normally I can type in startx and it'll take it from there.

---

### Post by eddied316 on 2012-10-30
Sorry to bump this but I'm really in a hurry to get it working. Can someone please help me access the GUI

---

### Post by eddied316 on 2012-10-31
This is my last post, maybe someone can help with a little more info.

This is the text I'm getting after entering "startx" to view the GUI:

root@Machine3:/# startx


X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
Current Operating System: Linux Machine3 2.6.32-042stab059.7 #1 SMP Tue Jul 24 19:12:01 M
SK 2012 i686
Kernel command line: quiet
Build Date: 29 August 2012  12:10:05AM
xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see [http://www.ubuntu.com/](http://www.ubuntu.com/)
support)
Current version of pixman: 0.26.0
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 31 09:30:22 2012
(==) Using system config directory "/usr/share/X11/xorg.conf.d"

Fatal server error:
xf86OpenConsole: Cannot find a free VT: Invalid argument


Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
Server terminated with error (1). Closing log file.
xinit: giving up
xinit: unable to connect to X server: No such file or directory
xinit: server error
root@Machine3:/#

---

### Post by snowpine on 2012-10-31
If you tell us what task you're trying to accomplish with your new server, I can try to walk you through it using terminal commands and/or help you find a link to more information. Unfortunately I cannot help you administer a server using the Ubuntu GUI because I have never done so, sorry.

---

