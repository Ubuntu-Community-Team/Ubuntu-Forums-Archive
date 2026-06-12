---
title: "Trail of frames when moving windows across screen"
date: 2005-02-12
forum: Desktop Environments
---

### Post by geofff on 2005-02-12
I've had this problem since first install. 

When I drag a window across the screen it leaves a trail of frames behind it which last for about 0.5secs - not critical but definitely not neat. 

I have AMD Athlon XP with Integrated VIA UniChrome Graphics (Chipset VIA VT8235 CE). I am now using the k7 kernel which has made a small improvement. 

I've not been able to find anything about this - except a suggestion via google of a problem with "backingstore" in "xorg.config". I've not been able to locate this within Ubuntu. However /etc/X11/XF86Config-4 quotes Identifier and Device as "VIA Technologies, Inc. VT8378 (S3 UniChrome) Integrated Video". 

I haven't a clue whether this is anything to do with my problem but thought it was worth mentioning!

Any offers much appreciated

---

### Post by tim1 on 2005-02-12
The XF86Config-4 and the xorg.conf are used by different X Servers, but they're pretty much compatible overall, since X.org is a fork of XFree86. So i suppose you try adding the  'backingstore' option to your XF86Config-4.

greets, tim

---

### Post by geofff on 2005-02-12
Thanks Tim

The googled page wasn't very specific. Do you think I just add "backingstore" at the end of the file and see what happens? I'm very new to this. 

I'm rather suprised that no-one else seems to have had this problem. My system is not unusual. It makes me think I have done something wrong on install,

---

### Post by egilpatr on 2007-04-05
I have just solvd this on Windows XP home:
Go to Control Panel, then Displays, then Appearance, and then Effects.  In that window is a box for "Show window content while dragging."  believe it or not, leaving the box CHECKED  solves the problem.

---

### Post by astromech on 2007-05-23
> **egilpatr said:**
> I have just solvd this on Windows XP home:
Go to Control Panel, then Displays, then Appearance, and then Effects.  In that window is a box for "Show window content while dragging."  believe it or not, leaving the box CHECKED  solves the problem.

Great that you solved it in windows but what about ubuntu?

---

