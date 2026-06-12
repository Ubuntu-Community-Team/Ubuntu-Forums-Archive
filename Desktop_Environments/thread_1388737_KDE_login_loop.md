---
title: "KDE login loop"
date: 2010-01-23
forum: Desktop Environments
---

### Post by kestrel1 on 2010-01-23
I have just installed Kubuntu 9.10, as I thought I should give KDE another go. I normally prefer gnome, but I better give KDE a chance. I have come across a problem in logging in though.
After a fresh install I reboot & try to login as normal, but after a couple of seconds I am taken back to the login screen. This happens no matter how many times I try. If I select Console login I am dropped back to the command line & can login, then I can type:
```
startx
```
& I get in to Kubuntu.
This is a bit of a pain to be honest & is fast putting me off of KDE. Never had this problem with Gnome.
I have updated Kubuntu & got the graphics drivers installed. I had read that if you use an xorg.conf file & set the virtual res to 1024x768 that may solve the problem, no such luck.
I have just re-installed it, so that I can start a fresh. I even thought that if I set it to auto login that may solve it, but no such luck. It attempts to login, but then gets kicked out to the login screen.
Has anyone come across this problem & managed to solve it? It would be useful, before I get rid of KDE & install Mint on that partition.
Cheers

---

### Post by Islington on 2010-01-23
logically I think the problem is with gdm or kdm (whichever you use)

---

### Post by kestrel1 on 2010-01-23
I would imagine it is kdm as this is a straight Kubuntu install, but how to fix it?

---

### Post by benerivo on 2010-01-23
Is there anything in /var/log/kdm.log that gives any clues to what happens when it crashes and restsarts?

---

### Post by kestrel1 on 2010-01-23
Here is the contents of the kdm.log file:
> ********************************************************************************
Note that your system uses syslog. All of kdm's internally generated messages
(i.e., not from libraries and external programs/scripts it uses) go to the
daemon.* syslog facility; check your syslog configuration to find out to which
file(s) it is logged. PAM logs messages related to authentication to authpriv.*.
********************************************************************************


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Kubuntu-01 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=f6aed7a5-a7a9-4ed3-a8a4-91b239d5dff8 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 23 18:41:59 2010
(==) Using default built-in configuration (30 lines)
(EE) open /dev/fb0: No such file or directory
error setting MTRR (base = 0xe8000000, size = 0x08000000, type = 1) Invalid argument (22)
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
error setting MTRR (base = 0xe8000000, size = 0x08000000, type = 1) Invalid argument (22)
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
error setting MTRR (base = 0xe8000000, size = 0x08000000, type = 1) Invalid argument (22)
 ddxSigGiveUp: Closing log

---

### Post by kestrel1 on 2010-01-24
Got this one sorted. Nothing to actually do with Kubuntu really, apart from it not liking my previous installs /home partition.
I didn't format the partition as I wanted to keep the files, but obviously one of the configs was messing with KDE. Saved my files & formatted the /home partition with a fresh install & I can login as normal.
Thanks to all for suggestions though.

---

