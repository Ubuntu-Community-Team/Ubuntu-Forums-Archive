---
title: "ScummVM  and Day of the tentacle"
date: 2007-07-22
forum: Gaming &amp; Leisure
---

### Post by Sain on 2007-07-22
Hi everyone!

Just installed ScummVM , and tried to play "Day of the Tentacle " with it, but for some reason Scumm exits as soon as i hit "start game". 

I haven't configured anything, left all options on default... Is there some particular setting i need to adjust for scumm to work on ubuntu? Does anyone have the same problem?

---

### Post by Shpongled303 on 2007-07-22
What version of ScummVM are you using and where did you get it? 1.0.0 is the latest version, I got mine from [www.getdeb.net](www.getdeb.net)

Also, are you sure you have all the files you need to run Day of the Tentacle? In that regards, try copying all the files off the DOTT CD again.

---

### Post by Sain on 2007-07-22
I have latest version of ScummVM, got it off their official site (debian package).
i'll try to copy the game again, but I doubt that's the problem. It works flawlessly on windows... I have diskette version of the game

---

### Post by walkingbeard on 2007-07-22
I have this problem too.  I think that it's because ScummVM is having trouble finding the MIDI device.

---

### Post by Shpongled303 on 2007-07-22
Sorry, no idea... I just installed ScummVM 0.10.0 from [www.getdeb.net](www.getdeb.net) and it's working fine -- got DotT straight from the DOS CD. All others running as well with sound and MIDI.

Any other games or just DotT that doesn't work?

---

### Post by hikaricore on 2007-07-22
Launch ScummVM from a terminal and follow the same condition that is currently causing it to crash.
If there is any error output in the terminal window, copy and paste it here, then maybe someone can help.  ^_^

---

### Post by Sain on 2007-07-23
OK, I've reinstalled Scummvm with using package from GetDeb. Now it works fine in window mode, but sooner or later crashes in fullscreen. 

This is what terminal says: *Segmentation fault (core dumped) *

On most settings it will not start in fullscreen, and when it does, it's only in upper-left corner, and it's unplayable; graphics go crazy when i enter menu, and then freezes entire system. :-?

---

### Post by hikaricore on 2007-07-23
> **Sain said:**
> OK, I've reinstalled Scummvm with using package from GetDeb. Now it works fine in window mode, but sooner or later crashes in fullscreen. 

This is what terminal says: *Segmentation fault (core dumped) *

On most settings it will not start in fullscreen, and when it does, it's only in upper-left corner, and it's unplayable; graphics go crazy when i enter menu, and then freezes entire system. :-?

Ok so at this point it's probably a video card/driver issue.

What type of hardware do you have?  What version of Ubuntu are you running?  32bit or 64bit?

^_^

As much info as possible incase anyone who has had a similar problem knows a work around.

---

### Post by Sain on 2007-07-25
My PC: Pentium4 @ 3.46 GHz 
            Abit AA8 i925x motherboard
            Nvidia 7800GT card
            2x1 GB Crucial DDR2 memory

Graphics driver is... well, proprietary driver that's in repositories; nvidia-glx-new package...
Ubuntu is 7.04, 32-bit

I dont know what else matters... I'll try with new drivers, but i hate installing graphics driver, as X window crashes nearly every time i do that :)

---

### Post by ARTO^UK on 2007-07-25
DoTT is my favourite game ever, just thought I'd throw that in there. Eagerly awaiting the fan game DoTT2 ([www.dott2.de](www.dott2.de))

---

### Post by bramvandijk on 2007-08-03
This happens to me too. The simple workaround is starting the game in windowed mode, then pressing Alt + Enter, and it works, full screen and all...

---

### Post by nick1985 on 2008-06-09
Hey everyone, I recently downloaded day of the tentacle, and scum (alongside monkey island 1 & 2) was just wondering, when i get to the super battery diagram, and select what needs to be done (according to the instructions in the game folder) it freezes when i click on the right hand corner. ive gone over it again and again, and still no luck. was wondering if anyone might be able to assist. 

thanks, 


Nick

---

