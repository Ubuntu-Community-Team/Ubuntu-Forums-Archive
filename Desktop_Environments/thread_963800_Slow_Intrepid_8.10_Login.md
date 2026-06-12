---
title: "Slow Intrepid 8.10 Login"
date: 2008-10-30
forum: Desktop Environments
---

### Post by aramadia on 2008-10-30
I noticed that logging in takes significantly longer than hardy.
After entering password it takes about 2s to show the wallpaper, but about 25s to load gnome.  Previously it only took approximately 5s to login in hardy.

I did some tests and gnome-failsafe takes just as long, but wmii takes less than 1s.  I also removed as many startup programs from sessions as possible.

Are other people experiencing this and is there a quickfix?

System:
New install of Ubuntu 8.10 from CD
T7500 2GB Ram (no swap) Seagate 7200.3 (relatively fast 7200rpm laptop hd)

EDIT (Workaround)
The bug has to do with compiz-fusion. In order to login quickly go to System->Preferences->Appearance->Visual Effects and set it to None.
Registered bug in launchpad: [https://bugs.launchpad.net/ubuntu/+bug/291467](https://bugs.launchpad.net/ubuntu/+bug/291467)

---

### Post by aramadia on 2008-10-30
After messing around with stuff apparently here is a weird solution.

What happened was after logging in, my computer sat there with virtually no activity for about 8s before starting the login process.  I disconnected everything connected to my computer and unchecked gnome-wm from sessions.  I login and it loads everything straight away though the desktop was ugly.  I rechecked everything in sessions and now the login is responsive and under 15s which is acceptable.

---

### Post by Dark Ocean on 2008-10-30
I have the same problem, I did a upgrade from hardy. When logging in, it takes much longer as usual.

---

### Post by Dalle85 on 2008-10-30
Ditto... Experiencing the exact same issue! Using Hardy, it took 5-10 secs to log in with my wallpaper emerging virtually instantly, after upgrading to Intrepid, it takes about 20 seconds before anything happens! When I hit "enter" from log in, the screen turns into that "ubuntu-brown" color and then it just seems to stop doing anything for 20 secs and then suddenly, the welcome sound plays and it starts up in 4-5 secs...

The computer is a T7300 Core2Duo 2.0 GHz, 2 Gb RAM, 8600 GS (256 mb), 7200 RPM HDD... So I don't think it is lack of performance which is the issue.

---

### Post by smirnoff76 on 2008-10-30
I have also found login incredibly slow taking 15 to 20 seconds before doing a thing. Disable gnome-gm and loads in substantially quicker but as aramadia says ugly. Re-enable the gnome-gm back to 15/20 wait?

---

### Post by Dalle85 on 2008-10-30
Okay, so I'm a bit of a noob when it comes to Ubuntu, but looking through the Log-files, I've found these three lines in the deamon.log which seems to appear on each start-up and it lasts for about 20 seconds:

> Oct 30 21:43:34 morten-laptop x-session-manager[6274]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Oct 30 21:43:45 morten-laptop x-session-manager[6274]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Oct 30 21:43:55 morten-laptop x-session-manager[6274]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 

Does this have anything to do with this issue or am I just wasting everybodies time on this?

---

### Post by Queue29 on 2008-10-30
Iv'e had this 'problem' too, but look at it this way: It's still faster than Vista. :cool:

---

### Post by aramadia on 2008-10-30
I have the same messages too:

Oct 30 23:48:33 m1530 pulseaudio[15958]: pid.c: Stale PID file, overwriting.
Oct 30 23:48:33 m1530 pulseaudio[15958]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Oct 30 23:48:33 m1530 pulseaudio[15958]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
**Oct 30 23:48:44 m1530 gnome-session[15895]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout **
Oct 30 23:48:44 m1530 pulseaudio[15958]: module-x11-xsmp.c: X11 session manager not running.
Oct 30 23:48:44 m1530 pulseaudio[15958]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

Clearly intrepid wasn't ready for release.  The problem is still recurring.

---

### Post by aramadia on 2008-10-30
Fixed!

Just figured it out.  The bug has to do with compiz-fusion.  In order to login quickly go to System->Preferences->Appearance->Visual Effects and set it to None.

I wonder if this is the same bug here:
[https://bugs.launchpad.net/ubuntu/+bug/259385]("https://bugs.launchpad.net/ubuntu/+bug/259385")

---

### Post by Dark Ocean on 2008-10-31
This is not really a fix, but merely a workaround. If I actually want to use compiz-fusion I've to enable it  everytime I log in?
At least when I want a fast login. :confused:

---

### Post by Dalle85 on 2008-10-31
Hmm... Seems to work, but I too think that you should be able to run Compiz without this kind of hickups! But if it has something to do with Compiz, I wonder if it is the same bug that is the cause of the window animations not working?! They worked perfectly well in Hardy, but now... Nada... No matter what I do to get them up and going, nothing happens.

---

### Post by jdeslip on 2008-10-31
The problem is with compiz-fusion, but how exactly is it "SOLVED"??  Identifying the problem is not the same as fixing it.  I have found a better work around then disabling compiz.  Turn effects off in the appearance setting but having fusion-icon added to the list of programs that Gnome runs at startup.  Is there a bug report for this issue?

---

### Post by Dalle85 on 2008-11-01
I have opened a bug report on launchpad regarding this issue since I believe the problem has not been solved, merely identified!

Bug report:

[https://bugs.launchpad.net/ubuntu/+bug/292376](https://bugs.launchpad.net/ubuntu/+bug/292376)

So lets see what they say...

---

### Post by sarath_it on 2008-11-02
Can you all confirm this:

You have an extremely small xorg.conf file, and CPU usage for xorg is relatively high (3-7%)


Other charecteristics extremely small  xorf.conf, high CPU (relatively) for xorg.conf

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by Dalle85 on 2008-11-02
It does seem like xorg is using quite a bit of CPU power, but there is nothing wrong with my Xorg.conf... Looks like update manager have commented out some configurations, but these have to do with my touchpad and keyboard, not screen, it says "Commented out by update manager, using HAL instead"... So I guess they transferred mousepad and keyboard support to the Hardware Abstraction Layer...

---

### Post by macabro22 on 2008-11-02
> **aramadia said:**
> I have the same messages too:

Oct 30 23:48:33 m1530 pulseaudio[15958]: pid.c: Stale PID file, overwriting.
Oct 30 23:48:33 m1530 pulseaudio[15958]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Oct 30 23:48:33 m1530 pulseaudio[15958]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
**Oct 30 23:48:44 m1530 gnome-session[15895]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout **
Oct 30 23:48:44 m1530 pulseaudio[15958]: module-x11-xsmp.c: X11 session manager not running.
Oct 30 23:48:44 m1530 pulseaudio[15958]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

Clearly intrepid wasn't ready for release.  The problem is still recurring.


I also get ```
x-session-manager[5854]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout

```

And I also get ```
x-session-manager[5854]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout
Starting g15daemon: 
```

in .xsession-errors.

I smell a fish.

---

### Post by jdeslip on 2008-11-03
I also have this in my log 

WARNING: Application 'gnome-wm.desktop' failed to register before timeout

And turning off compiz also speeds up the login for me (tremendously).  I am wondering if everyone who has this issue did a dist-upgrade from hardy.  Perhaps the problem is with some misconfiguration of Gnome?

---

### Post by sarath_it on 2008-11-03
I dont think its the problem with Compiz either. Neither is gnome-wm my prime suspect. I think this is an issue with X itself. 

Can you confirm there is an entry in syslog when you start up, and right before login screen comes up, the screen flickers **twice**? 
```
WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

```

---

### Post by etlgfx on 2008-11-05
I have the same slowness. I however did a *clean install* of 8.10. Compiz never used to load this slowly in the last 3 ubuntu releases...

---

### Post by macabro22 on 2008-11-06
I found a bug report implicating the slow login time with bad pulseaudio implementation (or something of the sort). There seems be to a patch that solves the issue, but I don't want to compile stuff and ****.

If anyone wants to try, please report back: [https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/276072/](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/276072/)

---

### Post by jdeslip on 2008-11-06
Sarath.  I do not have that message in my syslog...

---

### Post by ramblin' wreck on 2008-11-23
I just upgraded to 8.10, and after finally being able to get my ethernet card registering quickly, I hoped login would be sped up... nope. I'm running a great ATI card, Wolfdale E8400 core 2 duo... etc... etc... it gets stuck on the visual effects load.

I can't even get my webcam to work anymore. I'm just gonna deal with the slow login times until an update comes along. Really, I almost never need to logout on my personal desktop.

---

### Post by abhiroopb on 2009-03-20
Still very slow for me to login (started a new thread before I saw this: [http://ubuntuforums.org/showthread.php?t=1101385](http://ubuntuforums.org/showthread.php?t=1101385))

---

### Post by Schwalenberg on 2009-03-20
I have the same  "Application 'gnome-wm.desktop' failed to register before timeout" error. Except my gnome desktop will not work at all, it is just a blank screen. It has been this way since the latest update. It was fine before that, but now that it does this I have been using a command line ever since. I can still type firefox --display :0 then hit cntrl-alt-f7 and it will be running fine, but I have no desktop, no "start menu" or any of those things. The upside is I have been learning much about Linux, the downside is no GUI. Not sure what happened or how to fix it.

---

