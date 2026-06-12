---
title: "Dell D810 Laptop"
date: 2005-12-13
forum: Desktop Environments
---

### Post by Darksun on 2005-12-13
I have a Dell Latitude D810 laptop with the dock, if I install Ubuntu on the laptop, dock free everything is cool, if I dock the laptop I lose sound...anyone else having issues with the Dell docks?:confused:

---

### Post by sockrebel on 2005-12-29
I have had a problem with sound on the d/port for a couple of years, and I have yet to find a solution. (similar, but not sure if the same issue)

Plugging speakers into the headphone jack on the dock mutes the laptop speakers, but speakers do not output sound.  Plugging speakers into the laptop's headphone jack works though.  Without any external speakers plugged in, laptop speakers work when docked.

I have a d410 and d610 (and previously a d600), which I dock with this problem.  This problem isn't ubuntu-specific (I had it with Fedora and have seen other cases, too).  I just got a MediaBase for the d410 and the same thing happens.

I have tried messing with all of the alsamixer settings to no avail.

I would greatly appreciate any solutions suggestions.

Thanks!

p.s. the jack works fine on Windows.

> I have a Dell Latitude D810 laptop with the dock, if I install Ubuntu on the laptop, dock free everything is cool, if I dock the laptop I lose sound...anyone else having issues with the Dell docks?

---

### Post by sockrebel on 2005-12-29
found the solution:
The issue was that by default alsa outputs on the digital output of the d/port. if you go into alsamixer and turn down "IEC958 Playback AC97-SPSA" all the way, and make sure that "IEC958" is not muted, the analog port will work.

> Plugging speakers into the headphone jack on the dock mutes the laptop speakers, but speakers do not output sound. Plugging speakers into the laptop's headphone jack works though. Without any external speakers plugged in, laptop speakers work when docked.

I have tried messing with all of the alsamixer settings to no avail.

---

### Post by desmondo on 2007-04-24
In Feisty Fawn, I had to go into Volume Control (by clicking the volume icon in the status area of the desktop), select Preferences, check the box next to IEC958, and then I got a tab "Switches" where I could check a box next to IEC958.

Thanks for your help!

---

