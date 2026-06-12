---
title: "xscreensaver not locking"
date: 2013-09-16
forum: Desktop Environments
---

### Post by DavidBiesack on 2013-09-16
I'm running Xubuntu 13.04 with an xfce4 session.
I start xscreensaver in my startup script (not via xfce4 session config) and while I'm at my desk, 
xscreensaver does kick in and work as expected if I'm idle for a few minutes.
But very frequently, it stops working: even though the xscreensaver
process is running, it no longer blanks or locks the screen. 
I'll return to the office after being away past the timeout, and the screen is not locked.

I started a process to watch it :

```
xscreensaver-command -watch  >| ~/.log/xsceensaver.log 2>&1 &
```

and you can see from this excerpt how it "stopped" on Thursday until I edited my prefs today,
which seemed to kick it back into normal mode, locking at 11:38 this AM.

```
BLANK Thu Sep 12 14:13:33 2013
LOCK Thu Sep 12 14:13:33 2013
UNBLANK Thu Sep 12 14:24:49 2013
BLANK Thu Sep 12 14:31:44 2013
UNBLANK Thu Sep 12 14:31:46 2013
BLANK Thu Sep 12 14:40:46 2013
UNBLANK Thu Sep 12 14:40:50 2013
BLANK Mon Sep 16 11:38:11 2013
RUN 1 1
RUN 142 1
RUN 142 142
UNBLANK Mon Sep 16 11:38:29 2013
BLANK Mon Sep 16 11:46:40 2013
LOCK Mon Sep 16 11:46:40 2013
UNBLANK Mon Sep 16 11:55:41 2013
```

I've done all the system updates, rebooted, etc. yet this problem persists

My screensaver is GLMatrix which has worked fine for a couple years.

I'm not running any fullscreen apps that should disable the screensaver,
but I am running a Windows 7 VM in VMWare Player (running vmplayer unity
mode) and have a couple Windows apps running in X windows (Outlook,
Lync). I don't have any hot corners set to affect (disable) the screen saver
(I use openbox window manager)

---

