---
title: "gnomes overwrites dpms settings, even gnome is not used"
date: 2007-09-29
forum: Desktop Environments
---

### Post by kultex on 2007-09-29
Gnomes new energy settings are annoying -  they are overwriting xset, even you do not use gnome.  I am using Ubuntu-Studio feisty with Xubuntu desktop - I started Gnome only once to install the Xubuntu dektop. 
In XFCE I discovered, that the monitor of my X31 Thinkpad does not really turn off - the back light was always on - the .xscreensaver  file was perfect configured.  I downloaded the  Xubuntu desktop.iso - configured .xscreensaver the same way as in my Ubuntu-Studio and there the screen turns off perfect.

Ok - I thought, I uninstalled xscreensaver, because I do not need it and configure xset all the time manually, but this increased the problem - after some minutes, my xset dpms 60 100 120 was all the time overwritten to Standby: 0    Suspend: 0    Off: 0 and the the screen turned black after approx. 10 minutes with the same problem, that the back light does not turn off.

What was overwriting my dpms options? - Perhaps gnome? I started gnome and found out, that there is no possibility to set correct  dpms settings - in Ubuntu 6.10 it still works perfect - in 7.04 not - the reason is, that gnome switched from xscreensaver to gnome-screensaver

ok - I uninstalled all gnome packages and now the dpms settings are not overwritten any more, but still they are not functioning. The screen turns black after approx. 10 minutes with the same problem, that the back light does not turn off.

i have no more idea

regards kultex

---

### Post by Gammell on 2008-01-12
I don't know about all your overwriting problems, but I used to have a similar problem with the on my thinkpad. If I remember correctly it turned out to be a screensaver/DPMS issue, what does ```
xset q
``` show for the ***Screen Saver:*** and ***DPMS (Energy Star):*** entries?

---

### Post by nogasbiker on 2008-01-21
Actually, the OP is correct.  The dpms settings as shown by xset are overwritten once an hour or so.  There are many threads about the lack of a real screensaver, where the monitor is actually placed in a low power state (i.e. the backlight is turned off).

Many people suggest setting dpms via 'xset dpms <time1> <time2> <time3>'.  It seems to work, everyone thinks it is all better.  But the dpms settings get overwritten to 0 0 0, which means no dpms.

All the threads here and elsewhere don't show a solution.  My workaround is a script that wakes up every ten minutes and blasts the dpms settings the way I want them.  I also query the dpms settings and write a timestamp, the output is pasted below for everyone's amusement ;)

But clearly, there IS a problem...  :O


Mon Jan 14 10:03:53 PST 2008 Managing status of dpms
  before:   Standby: 0    Suspend: 0    Off: 0
  after :   Standby: 180    Suspend: 180    Off: 180
  sleep 600...   awakened at Mon Jan 14 10:13:53 PST 2008

Mon Jan 14 10:13:53 PST 2008 Managing status of dpms
  before:   Standby: 180    Suspend: 180    Off: 180
  after :   Standby: 180    Suspend: 180    Off: 180
  sleep 600...   awakened at Mon Jan 14 10:23:53 PST 2008

Mon Jan 14 10:23:53 PST 2008 Managing status of dpms
  before:   Standby: 0    Suspend: 0    Off: 0
  after :   Standby: 180    Suspend: 180    Off: 180
  sleep 600...   awakened at Mon Jan 14 11:34:20 PST 2008

Mon Jan 14 11:34:20 PST 2008 Managing status of dpms
  before:   Standby: 0    Suspend: 0    Off: 0
  after :   Standby: 180    Suspend: 180    Off: 180
  sleep 600...   awakened at Mon Jan 14 11:44:20 PST 2008

Mon Jan 14 11:44:21 PST 2008 Managing status of dpms
  before:   Standby: 180    Suspend: 180    Off: 180
  after :   Standby: 180    Suspend: 180    Off: 180
  sleep 600...   awakened at Mon Jan 14 11:54:21 PST 2008

Mon Jan 14 11:54:21 PST 2008 Managing status of dpms
  before:   Standby: 180    Suspend: 180    Off: 180
  after :   Standby: 180    Suspend: 180    Off: 180
  sleep 600...   awakened at Mon Jan 14 12:04:21 PST 2008

Mon Jan 14 12:04:21 PST 2008 Managing status of dpms
  before:   Standby: 180    Suspend: 180    Off: 180
  after :   Standby: 180    Suspend: 180    Off: 180
  sleep 600...   awakened at Mon Jan 14 12:14:21 PST 2008

Mon Jan 14 12:14:21 PST 2008 Managing status of dpms
  before:   Standby: 0    Suspend: 0    Off: 60
  after :   Standby: 180    Suspend: 180    Off: 180
  sleep 600...   awakened at Mon Jan 14 12:24:21 PST 2008

Mon Jan 14 12:24:21 PST 2008 Managing status of dpms
  before:   Standby: 180    Suspend: 180    Off: 180
  after :   Standby: 180    Suspend: 180    Off: 180
  sleep 600...   awakened at Mon Jan 14 12:34:21 PST 2008

Mon Jan 14 12:34:21 PST 2008 Managing status of dpms
  before:   Standby: 0    Suspend: 0    Off: 0
  after :   Standby: 180    Suspend: 180    Off: 180
  sleep 600...   awakened at Mon Jan 14 12:44:22 PST 2008

Mon Jan 14 12:44:22 PST 2008 Managing status of dpms
  before:   Standby: 180    Suspend: 180    Off: 180
  after :   Standby: 180    Suspend: 180    Off: 180
  sleep 600...   awakened at Mon Jan 14 17:33:32 PST 2008

Mon Jan 14 17:33:32 PST 2008 Managing status of dpms
  before:   Standby: 0    Suspend: 0    Off: 0
  after :   Standby: 180    Suspend: 180    Off: 180
  sleep 600...

---

