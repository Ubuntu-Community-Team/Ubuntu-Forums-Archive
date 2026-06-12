---
title: "ATI BigDesktop - Mirrored"
date: 2007-04-25
forum: Desktop Environments
---

### Post by harusp3x on 2007-04-25
I would like to enable BigDesktop so X spans the entire length of my two montiors, however it is currently only mirroring one onto the other. 

I have the following code inserted in my xorg.conf file

```
Option "DesktopSetup"  "horizontal" #Enable Big Desktop
Option "Mode2"         "1024x768" #Resolution for second monitor
Option "DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CRT, AUTO
Option "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
Option "HSync2" "65" #This sets the horizontal sync for the secondary display. 
Option "VRefresh2" "75" #This sets the refresh rate of the secondary display.
```

_Thanks.

---

### Post by mrvertigo on 2007-04-27
good question, i will be interested to see a resolution to this one

---

### Post by harusp3x on 2007-04-29
Still having the same problem. Any ideas? :(

---

### Post by mrvertigo on 2007-04-30
heck i decided to get annother monitor to try it out and i too am having the same problem
wish i could help

---

