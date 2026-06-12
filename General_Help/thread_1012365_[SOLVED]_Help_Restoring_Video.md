---
title: "[SOLVED] Help Restoring Video"
date: 2008-12-15
forum: General Help
---

### Post by chaplanger on 2008-12-15
Resolution headache:
Hardware:
Monitor is a Dell 1704FPV (Flat Panel)
Video Card: NVIDIA GeForce 6600 GT


I was experimenting in trying to get my Ubuntu (8.04) to actually accept the resolution of my Dell 1704FPV monitor (maybe even a 1280 x 1024 setting) 

I adjusted the settings from a generic monitor to my monitor, choose the resolution and may have chosen too high of a refresh rate -- when I restarted Ubuntu the display is a mess. 

I have a frazzled screen that seems to have 4 narrow columns of the initial desktop.  The image is highly frazzled (unable to clearly see or read anything).  It is as if the resolultion or frequency adjustment is too high.

Obviously I need to reset the settings that were changed but I don't know how.

I thought I would simply boot into safe mode -- but when I try this it goes into a blue screen of diagnostics that never seem to end (last time it was going on over two hours and had not completed)

How do I correct this resolution mess?
I do have a live CD that can be used to boot into a Linux session, but I have no idea what to do from there.

Any help will be appreciated.  Once again, please take me step by step (novice here).

Thanks!

---

### Post by eBoxNet on 2008-12-15
did you try to reconfigure xorg?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by chaplanger on 2008-12-15
I haven't tried this -- how do I do this when I can't seem to get to a terminal session? (safe mode isn't working see above).

---

### Post by eBoxNet on 2008-12-15
try to normal boot your machine and when it boots up hit Ctrl+Alt+F1

---

### Post by chaplanger on 2008-12-15
Ok, I see what you are saying and this may have worked. . . 

However, I resolved this issue by reformatting the drive and installing Ubuntu 8.10 on the newly reformatted drive.

Now I just need to add my programs back -- otherwise 8.10 is much nicer than 8.04 -- my video card is recognized and the settings are accurate!  Wohoo.  All in all a small amount of pain (reinstalling programs) for a lot of gain.

---

### Post by jah_60025 on 2008-12-16
I'm on Ubuntu 8.10, and had video problems that, I too only solved by reinstalling.  But not exactly the same problem -- I was trying the display at the various resolutions available to me, and one resulted in a completely blank screen -- and I couldn't get it to reset to a useable resoltuion -- none of the command-based solutions worked for me.  So I mapped out the key-stroke path to get back to the one resolution that DID work, and I think that would cover me if I inadvertently get the issue again -- and I think this might help with any resolution-caused display problems.

[> = right arrow, < = left arrow, ^ = up arrow, v = down arrow - is just a spacer; v*17 means 'down arrow 17 times']
ALT-F1 - > - > - v - > - v*17 - ENTER (and wait a few seconds) - TAB - ^ (until you hear a beep) - ALT-A | ESC

So after the TAB, you're in the resolution menu, so you can select however many clicks to make to try different resolutions -- for me the first in the list worked, so I use that as my point of reference.

Reminds me of video game cheat codes...

Anyway, I'm a complete newbie to Linux, so there are surely slicker solutions, but this is my current safety net.

Cheers!

jh

---

