---
title: "Saucy, Ubuntu-gnome, classic, gnome-panel"
date: 2013-10-26
forum: Desktop Environments
---

### Post by edgreenberg on 2013-10-26
I've just installed a copy of Ubuntu-Gnome Saucy Salamander.   Looks pretty good, but I'm trying to set it up it to my habits and note that Panels have changed.   I have two monitors. There is something running on the top and bottom of the rightmost monitor that loks like a panel, but it doesn't behave like a panel.  For one thing, you can't alt-rightclick on it and get the ability to add Panel applets. 
[FONT=courier new]ps ax | grep panel[/FONT] yields this:
```
edg@arthur:~$ ps ax | grep panel
 1677 ?        Sl     0:00 /usr/bin/ibus-daemon --replace --xim --panel disable
 3445 pts/0    S+     0:00 grep --color=auto panel
edg@arthur:~$ 
```

I did[FONT=courier new] sudo aptitude install gnome-panel[/FONT] as suggested in another post, and it installed many packages. [FONT=courier new]  dpkg -l | grep panel[/FONT] now shows 
```
edg@arthur:~$ dpkg -l | grep panel
ii  gir1.2-panelapplet-4.0                    1:3.6.2-0ubuntu15                   i386         GObject introspection for the GNOME Panel Applet library
ii  gnome-applets                             3.5.92-0ubuntu3                     i386         Various applets for the GNOME panel - binary files
ii  gnome-applets-data                        3.5.92-0ubuntu3                     all          Various applets for the GNOME panel - data files
ii  gnome-panel                               1:3.6.2-0ubuntu15                   i386         launcher and docking facility for GNOME
ii  gnome-panel-data                          1:3.6.2-0ubuntu15                   all          common files for the GNOME Panel
ii  indicator-applet-complete                 12.10.2+13.10.20130924.2-0ubuntu1   i386         Clone of the GNOME panel indicator applet
ii  libindicator3-7                           12.10.2+13.10.20130913-0ubuntu1     i386         panel indicator applet - shared library
ii  libpanel-applet-4-0                       1:3.6.2-0ubuntu15                   i386         library for GNOME Panel applets
ii  python-ubuntuone-control-panel            13.09-0ubuntu1                      all          Ubuntu One Control Panel - Python Libraries
ii  ubuntuone-control-panel                   13.09-0ubuntu1                      all          Ubuntu One Control Panel
edg@arthur:~$ 
```

I don't think I'm using any of what I installed, even though I've logged out and in, and also rebooted.  

How do I get traditional panels working again?

Thanks, 

Ed Greenberg
Glens Falls, NY USA

---

### Post by Frogs Hair on 2013-10-26
Flash back is the old Fall-back session and Classic is an additional Gnome shell session The key binding won't work in that session because there is no add to panel menu. Classic has a window list for open application switching and a workspace indicator .```
 sudo apt get install gnome-session-flashback 
```

---

### Post by kansasnoob on 2013-10-26
> **Frogs Hair said:**
> Flash back is the old Fall-back session and Classic is an additional Gnome shell session The key binding won't work in that session because there is no add to panel menu. Classic has a window list for open application switching and a workspace indicator .```
 sudo apt get install gnome-session-flashback 
```

+1!

There seems to be a lot of confusion about the evolution of "GNOME classic" :(

In Oneiric, Precise, and Quantal there were "classic" and "classic (no effects)" sessions based on GNOME's fallback mode which was expected to die, but Edubuntu decided to support it for their LTSP installs which is good news for us.

Then to accommodate GNOME's new classic gnome-shell session at the request of Red Hat we were forced to replace the name "classic" with "fallback" in Raring.

Then to further complicate things the devs changed the session name from "fallback" to "flashback" in Saucy.

How could anyone possibly be confused :lolflag:

---

### Post by edgreenberg on 2013-10-26
Many thanks for the pointer. Looks like a winner. I'm not running Fallback 2D.  Not sure why plain Fallback doesn't ever get past a blank screen with a mouse pointer,  but I'm happy. 

Ed

---

