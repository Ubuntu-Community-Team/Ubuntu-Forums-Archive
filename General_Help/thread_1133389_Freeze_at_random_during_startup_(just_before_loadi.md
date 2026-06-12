---
title: "Freeze at random during startup (just before loading gdm) [Xubuntu 9.04]"
date: 2009-04-22
forum: General Help
---

### Post by remjg on 2009-04-22
Hey all,

I've just installed Xubuntu 9.04 one week ago and I face a strange problem when starting sometimes (let's say every third time).
The system freeze just before loading GDM (the progress bar is almost completed). When it's the case, the system is completely frozen and the hard drive stop after a while (impossible to switch to a terminal).
I tried to press Ctrl-Alt-F1 to get some output but the last thing that is written is "Starting HAL Abstraction Layer (...)" (or something like that).

My laptop is around 3-year-old (Acer Travelmate 8100, Pentium M, Ati X700) and was working well since Ubuntu Dapper.

So how can I get more information to solve my issue?
Thank you for your help!

Rémi.

---

### Post by remjg on 2009-05-13
Still the same issue. Any idea?

---

### Post by Kasumi on 2009-05-18
I get this freezing thing as well in Xubuntu 9.04 it didn't do this before but now its every time.  The only way I can bypass this freeze is when the grub menu loaded I select the kernel with recovery mode then I select normal boot its boots fine.  Doesn't freeze while loading the gdm.  Though this happens too when I log out from account and when it trys to load the gdm it freezes again.  Can anybody help

---

### Post by Mark Tomlinson on 2009-06-03
Kasumi, I have exactly the same problem - letter for letter.  Even the work-around is exactly the same.  GDM freezes if I reboot, but if I go to the Grub menu and select recovery mode and then normal boot everything comes up fine.  This happens every time since I upgraded to Xubuntu 9.04.

I can still access the computer via SSH while the console is disabled, so the problem is clearly with Gnome.  Following some advice for similar problems, I ensured that everything in my home folder is owned by me, but that didn't help.

Ubuntu is not my primary OS, so I'm still rather a n00b and helpless to diagnose the problem.  Any suggestions are welcome.

---

### Post by Kasumi on 2009-06-03
I'm still noobish from xubuntu 7.10, though I would want to help but I don't know what log file that will show error when it loads the gdm or at the gdm and I'm not good at reading log files.  Which kinda makes it hard for me to solve my own problem.  Though I been living with the error hehe.  Also don't think there is a bug report for this either. I never did that either.

---

### Post by Mark Tomlinson on 2009-06-03
Well, I found the log.  Maybe we can help each other here.  The logs are in /var/log/gdm.

When I reboot and GDM fails, this is the log:
```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Elroy 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May 29 07:26:23 2009
(==) Using config file: "/etc/X11/xorg.conf"
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
get fences failed: -1
param: 6, val: 0
get fences failed: -1
param: 6, val: 0
 ddxSigGiveUp: Closing log
```
When I boot in recovery mode and GDM works properly, the log looks like this:
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Elroy 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 30 12:22:22 2009
(==) Using config file: "/etc/X11/xorg.conf"
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
get fences failed: -1
param: 6, val: 0
get fences failed: -1
param: 6, val: 0
```  See it?  The one difference is the line "ddxSigGiveUp: Closing log" in the failed attempt.

I have no idea what that means.

---

### Post by Kasumi on 2009-06-03
Best thing to do is file a bug report, since this is way out of my league.  I hope they fix the problem if that is the cause of the error.

---

### Post by Mark Tomlinson on 2009-06-06
Ok, something that was bothering me.  (Being a n00b and all).  We kept talking about GNOME and looking at GDM logs - but Xubuntu runs XFCE.  There were reasons I felt the problem was in GNOME, but it had to do more with staring blankly at log files and scrolling messages than any real debugging.

So I went to Settings > XFCE 4 Settings Manager > Session and Startup > Advanced and unchecked "Launch GNOME services at startup" under "Compatibility".  *That fixed it!*

So far I have not noticed any issues from shutting this off.  I was concerned that "VINO (VNC server for GNOME)" would not start, but it runs just fine.  Since I apparently don't need GNOME compatibility, I consider this a fix rather than a work-around.

Let me know if this corrects the problem for anyone else.

---

### Post by Jotham on 2010-02-01
I had a similar problem on Xubuntu 9.10 and your method solved it.
Thanks.

---

