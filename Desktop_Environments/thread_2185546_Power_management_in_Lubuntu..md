---
title: "Power management in Lubuntu."
date: 2013-11-03
forum: Desktop Environments
---

### Post by Azyx on 2013-11-03
Installed lubunutu 13.04 and updated to 13.10 for a few days ago. I think this error also was on 13:04, but not sure..

Anyway, which Power managent does Lubuntu use? Is it 'Xfce4 Power Manager'? Every time I try to activate it, it says it is not running. And a problem is when I close the lid on my ASUS eee PC 900  AND have the power-cord in (running on AC) my netbook go to 'Suspend' despite I have said do  'Nothing' under settings in Menue-->Preferences-->'Power Manager'.

There are so many chois of preferences and settings: 
Costumize look and feels
Desktop session setting
Openbox Configuration Manager
Screensaver Managment
Power Manager

Under Screensaver Management-->Advanced, there are a checkbox for 'Display Power Management', is that the same Power Management (Xfce4 Power Manager). But when I activate, there are completly different times to Standby, Suspend and Off, that I have in 'Xfce4 Power Manager'. In this box under Screensaver Management, there are also no diffents according to on batteri or AC

I wonder if there are som other 'Power manager' running who have other rules, than i specified in 'Xfce4 Power Manager'? It does not seems to start automatically during boot.  I may have installed someone else or that earlier versions of Lubuntu have had another 'Power manager'?

---

### Post by SonnyE on 2013-11-03
To check if xfce4-power-manager is running,  ps -e | grep xfce

If that doesn't show xfce4-power-man, or if Preferences > Power Manager doesn't open Xfce4 Power Manager settings, then try these instructions:

The file /home/username/.config/lxsession/Lubuntu/desktop.conf has a line that reads
power_manager/command=auto
(in the early versions of 13.10 that we're getting now.) If you edit that line to read
power_manager/command=xfce4-power-manager

then Lubuntu should run the Xfce4 Power Manager on boot and should let you edit the preferences for it under Preferences > Power Manager.

I don't have "Screensaver Management" as an option on my "Preferences" menu, but I have "Screensaver" because of installing XScreenSaver. I tried running XScreenSaver on Lubuntu 13.10 just now, then tried Preferences > Power Manager and that gave me the error message "Xfce4 Power Manager is not running, do you want to launch it?" So it seems like Lubuntu 13.10 can't run those two together. Ubuntu 13.10 with LXDE can run them together. I just now set them running against each other. The screensaver started at one minute, then the power manager turned off the display at two minutes, then after a few seconds the screensaver turned the display back on to keep showing the screensaver. After about ten minutes, the power manager put it into suspend.

(Posting from my old laptop in Lubuntu 12.04 so I can watch my new computer do that in the background.)

---

### Post by Azyx on 2013-11-03
Ok thanks :). Recognised that message also that it was not running. I think I will see tomorrow if I can get some help. I have upgraded also and I think I have installed gnomes power manager also. will check tomorrow.
/Cheers

---

### Post by Azyx on 2013-11-07
Thanx. I now run:

```
ps -e | grep xfce
```

And get 7 hit with [COLOR=#800080][/COLOR]xxxx ? 00:00:00 [COLOR=#800080]xfce[/COLOR]4-power-man

I change you ps command to

```
ps -e | grep [COLOR=#800080]power[/COLOR]
```

And get 7 hits with xfce4-[COLOR=#800080]power[/COLOR]-man and 
1 hit u[COLOR=#800080]power[/COLOR]d

It seems like xfce4-power-man are running.... but that do upowerd coming from? Could that be another power manager or are that connected to xfce4-power-man ?

When I run ```
ps -e | grep power 
``` on Ubuntu 12.04LTS s machine I get:

```
xxxx ?  00:00:00 upower
``` ;

there xxxx is a 4 figure integer.. pid?

/Cheers

---

