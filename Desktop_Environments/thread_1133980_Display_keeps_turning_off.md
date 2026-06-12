---
title: "Display keeps turning off"
date: 2009-04-23
forum: Desktop Environments
---

### Post by peterno3 on 2009-04-23
For some reason, by display keeps turning off every 10minutes or so if I don't move the mouse. I have the screen saver turned off, and "turn off display" and "sleep" set to never. I mainly use this computer for watching tv shows online, so it gets kind of annoying to have to nudge my mouse every few minutes to keep the video going. Thanks

---

### Post by Sam Lars on 2009-04-24
Try using xset to turn off screensaver...
```
xset -s off
```

---

### Post by peterno3 on 2009-04-26
I tried this, but it didn't help. I also used xset to turn off energy star settings incase this was the problem, but that didnt do it either. 
If it helps, i think the display is turning off, not going to screen saver because my screen turns blue instead of black. Any other suggestions?

---

### Post by Sam Lars on 2009-04-27
Could the BIOS or maybe monitor have a setting for that?

---

### Post by peterno3 on 2009-04-27
No, i don't believe it is either of those. I used to have xp and normal ubuntu before i wiped the drive and installed xubuntu, and it never did it then. I'm pretty sure that means it has to be a setting or software in xubuntu. oh yeah, i have 8.04 if that matters. i've tried upgrading, but for some reason it won't boot on my computer, so i have had to go back to heron.

Another thing i noticed is that this doesn't happen if i am watching videos in mplayer, but it does if im watching a flash video or not doing anything. This must mean that the computer still knows not to turn off the display if a movie is playing, right?

---

### Post by Sam Lars on 2009-04-27
Yeah, mplayer probably has some sort of inhibit feature that keeps it from kicking in.
I did some stuff with Xubuntu a little while ago and was trying to get the screensaver to turn off, and got a little confused about Xscreensaver vs. Gnome screensaver... and xset... any chance there's conflict between the X and Gnome screensavers?

---

### Post by peterno3 on 2009-04-27
Yeah, i guess thats a possibility. I didn't install the screen saver myself, but if it came installed or installed without me knowing that could be causing it. how would i go about trying to disable that one too?

---

### Post by Sam Lars on 2009-04-27
If you just installed Xubuntu, it should be fine.  I guess you could try stopping xscreensaver to see if when it's not running your display doesn't shut off.

---

### Post by peterno3 on 2009-04-28
I think that fixed it. I uninstalled both grub and xubuntu's screen saver, and it fixed the problem. Thanks

---

