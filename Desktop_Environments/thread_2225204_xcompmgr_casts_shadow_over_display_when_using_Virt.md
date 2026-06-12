---
title: "xcompmgr casts shadow over display when using VirtualBox seamless mode"
date: 2014-05-20
forum: Desktop Environments
---

### Post by DavidBiesack on 2014-05-20
I'm running XUbunto and recently upgraded from 13.10 to 14.04
 
VirtualBox 4.3.12 leaves a "shadow" artifact across my host display when I run a VirtualBox guest VM (Windows 7) in seamless mode. 


Here is a screenshot where you can see the effect on the right half of the desktop display.


[IMG]https://lh3.googleusercontent.com/-QiSAB_NGCw0/U3tY-UhVtHI/AAAAAAAAAHE/RCe6OeI0efQ/w1096-h411-no/desktop.png[/IMG]


I moved the (host) browser window so that it spans both monitors, you can see the shadow on top of the right side of it.
This shadow acts like another window - I can stack other host windows on top of it by selecting them, but  as soon as I select a guest window,
the shadow is moved above the native host windows. The guest windows (seamless) have no shadow.
If I change from seamless to scaled, this shadow disappears.


I run 


   xcompmgr -c -t-5 -l-5 -r4.2 -o.55


to allow some apps like conky to run with a transparent background. If I kill xcompmgr this shadow
goes away.


If I change from 


   xcompmgr -c -t-5 -l-5 -r4.2 -o.55


to


   xcompmgr -n -t-5 -l-5 -r4.2 -o.55
or
  xcompmgr -s -t-5 -l-5 -r4.2 -o.55


conky works and this large shadow is gone.
Before I upgraded XUbuntu to 14.04 I did not have this problem using xcompmgr

Is this a bug in xcompmgr ? In VirtualBox? X Windows? I don't know where to file this.

---

### Post by alexpage on 2014-06-17
I've had the same problem every couple of weeks under awesome window manager. I run xcompmgr with only the -c flag.  I haven't noticed the issue with virtualbox, but with seemingly random windows leaving a shadow just in their location on the screen.  Since it's so infrequent and I haven't noticed a trend in what causes it, I've just been killing and restarting xcompmgr when it happens.  I believe I tried running it with -n at some point and had either the same problem or a different one.  Maybe I'll try -s next time.

Also, I'm not sure if xcompmgr is being developed any more, so if that's where the bug lies, then ........ :(

---

