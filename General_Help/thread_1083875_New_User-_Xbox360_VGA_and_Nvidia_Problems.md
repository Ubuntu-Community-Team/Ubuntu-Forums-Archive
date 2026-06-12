---
title: "New User- Xbox360 VGA and Nvidia Problems"
date: 2009-03-01
forum: General Help
---

### Post by TonyD23 on 2009-03-01
Hey, I just installed Ubuntu 8.10 on my PC. This is the first time I've used Ubuntu, or any Linux variation. Everything has gone well except for two pretty big problems. 

1. I have my Xbox 360 connected to my monitor via a VGA cord. The sound for the 360 is played through the computers sound card. When I had Windows XP it worked, but now no sound will play on my Xbox. I can hear sound fine while on my operating system however.

2. I'm trying to install Nvidia 6 drivers and am coming across problems. I go to "Hardware Drivers" in system administration and select the driver I want to install. It starts the install process but freezes and 0%. 

3. *edit* This is a new problem that I thought I fixed but it's not. Every so often, randomly, Ubuntu will freeze completely. It doesn't matter what application I'm running it just happens. My keyboard and mouse are unfunctional and no key board short cut works. 

Thank you! Remember, I'm still a super scrub at this so keep it easy.

---

### Post by cariboo on 2009-03-01
> 2. I'm trying to install Nvidia 6 drivers and am coming across problems. I go to "Hardware Drivers" in system administration and select the driver I want to install. It starts the install process but freezes and 0%.


I have had the same problem. What I did was to install the driver using Synaptic Package Manager, then activate them, using System-->Administration-->Hardware Drivers.

Jim

---

### Post by TonyD23 on 2009-03-01
Sorry, I've been looking for fixes online for hours now and no luck. I don't know what that means. I went to that program you just posted and have had no luck.

---

### Post by TonyD23 on 2009-03-01
I typed installed something called envy and typed I believe envying- t (something like that, forget). Anyway, it came up with the options menu and the site told me to click the driver I needed to install. I typed 0 to install the 177 drivers and this came up. 

Dowloading the packages...
[===================================57.1%====>                                 ]result could not be parsed
Error in function pulse
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Envy/packagemanager.py", line 75, in pulse
    self.newObject.updateUi(percent)
  File "interface.py", line 65, in updateUi
    numHashes = int(round(numHashes))
TypeError: an integer is required
/usr/bin/envyng: line 4:  5546 Segmentation fault      sudo python interface.py
anthony@Anthony-Desktop:~$

---

### Post by TonyD23 on 2009-03-01
Wow, I uninstalled my drivers (since I didn't think any were actually installed). Now my font is huge and everything on my screen is super pixelated. This is stupid, lol, why does something so nominal on XP take so long on Ubuntu? That's not a low blow to anyone, I'm just really curious.

Hope this works out, liking the speed of this OS.

---

### Post by TonyD23 on 2009-03-01
EnvyG is now spazing out on me. It's going from 57% to 100% then back to 57 at a million flashes per second.

---

### Post by TonyD23 on 2009-03-01
I un-installed Ubuntu and installed Linux Mint. Seems to be practically the same thing with a different layout (to the n00b eye at least). Anyway, still having the same problems just different OS.

Life sucks.

---

