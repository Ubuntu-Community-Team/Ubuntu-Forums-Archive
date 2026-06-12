---
title: "How to force monitor into powersave mode?"
date: 2007-02-16
forum: Desktop Environments
---

### Post by NiksaVel on 2007-02-16
Hey all, 

I'm on gnome edgy and I have a comp which is on 24/7 but I directly access it only now and than...  and it has a separate monitor that is right next to the one where I usually play games and such...

Since the minimum for power saving setting to shut down monitor is 20min... it tends to get on my nerves that I am playing a game or studying while this monitor is on and distracting me for 20mins minimum...  or I accidentally move the mouse and it's up for another 20mins

To the topic :)   is there a command I can execute that will simply force the monitor into power saving mode upon execution?  Or at least a way to lower the minimum of 20mins for the monitor to shut down...   every now and than it seems that it refuses to shut off even after 20 minutes ... and it's on for more than an hour....   all I have running int he background is skype and kopete...



thanks in advance for all help!

---

### Post by moffa on 2007-04-19
Hi, try

```
 sudo xset dpms force standby 
```

---

### Post by NiksaVel on 2007-04-19
better late than never :)

it works, at least on my laptop...  will try on desktop tomorrow...


THANKS!

---

### Post by RedSquirrel on 2007-04-19
> **NiksaVel said:**
> Hey all, 

I'm on gnome edgy and I have a comp which is on 24/7 but I directly access it only now and than...  and it has a separate monitor that is right next to the one where I usually play games and such...

Since the minimum for power saving setting to shut down monitor is 20min... it tends to get on my nerves that I am playing a game or studying while this monitor is on and distracting me for 20mins minimum...  or I accidentally move the mouse and it's up for another 20mins

To the topic :)   is there a command I can execute that will simply force the monitor into power saving mode upon execution?  Or at least a way to lower the minimum of 20mins for the monitor to shut down...   every now and than it seems that it refuses to shut off even after 20 minutes ... and it's on for more than an hour....   all I have running int he background is skype and kopete...



thanks in advance for all help!


Have a look at the man page for xorg.conf:

```
man xorg.conf
```
You can manually set all of the times for various levels of power savings. In my case, I have an LCD monitor, so I have it blank after 5 minutes and off after 10 minutes. My *ServerLayout* section:

```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
[B]        Option  "BlankTime"     "5"
        Option  "StandbyTime"   "0"
        Option  "SuspendTime"   "0"
        Option  "OffTime"       "10"
[/B]EndSection

```


That's what I use for a screensaver, rather than running xscreensaver or gnome-screensaver. Works like a charm. Just be sure to restart X (Ctrl-Alt-Backspace) to make sure your new settings take effect.

---

