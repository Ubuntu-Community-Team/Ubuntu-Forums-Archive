---
title: "Odd Screensaver Problem."
date: 2006-11-03
forum: Desktop Environments
---

### Post by jso2897 on 2006-11-03
I have a wierd thing happening. My screensavers all work fine. My video drivers are enabled, and 3D rendering is working. But if I set the screensavers to "random", so that it rotates through different screensavers, after one or two it locks up, and locks up hard. Can't even get to command line with Ctl/Alt/bkspc or Ctl/Alt/F1, have to reboot with the power button. Choose one screensaver, and everything works fine. Wierd, huh? Any ideas? It's not exactly a huge deal.:cool:

---

### Post by jso2897 on 2006-11-03
I apologize for bumping this. It will be the last time - if I don't get any bites this time, I'll let it sink.:mrgreen:

---

### Post by JayTee on 2006-11-03
I ran into a problem with running the Busy Spheres screen saver. It worked fine with Metacity but when I installed XGL and Beryl Window Manager with Emerald Themes Manager I noticed the computer would have a hard lockup whenever the screensaver time interval passed. I'm using the latest Nvidia beta driver and Beryl 0.1.1 Trying to load the screen saver applet from System | Preferences would also lock up the system as it would want to show the current screensaver as a preview. I had to reboot and got immediately into the Beryl Manager and reset my Window Manager to Metacity to select none as a screensaver. Then I restarted Beryl as the Window Manager and went back into System | Preferences | Screensaver and tried different screensavers. The ones I tested that worked ok were all the GL ones, Pulsar, Slidescreen, Solarwinds, Sonar, Sierpinski 3D. Several others appeared to work but Busy Spheres was definitely causing grief.

---

### Post by jso2897 on 2006-11-04
Doesn't sound like the same bug. My screensavers (incl. Busy Spheres) are all working fine. It's the actual shuffle function of the "random" screensaver selection that causes my lockup. How or why, I have no idea - it seems like when I reboot, everything clears and there is no error report I can find. I would think there is a way to get error messages from previous sessions, but I haven't stumbled onto it yet.

---

