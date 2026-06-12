---
title: "Auto update problem - it locks up"
date: 2006-07-26
forum: Desktop Environments
---

### Post by drewbert on 2006-07-26
I have the following system:
AMD Athlon XP 2000+ (palomino core)
1GB DDR333 RAM
Nvidia Geforce 4 Ti4200 (128MB)
Audigy Platinum
MSI KT3 Mobo
80GB WD Harddrive (8MB Cache)
DLink Network card....

I Install from the live DVD and all seems fine...after booting into the fresh install it seems fine but it says there are like 190ish updates.....so I click install updates......things moove along smoothly ntil it gets to a package called GNOME PANEL (or something like that) then it hangs....everything freezes...the mouse doesn't respond, caps lock and num lock don't even turn the LEDs on on the keyboard and i wait 45 mins or so when this happens to see if it clears it's self up....it doesn't so I hit the reset button....on reboot it seems fine until after prompting for the username and password....then the screen turns to that default brown color (solid no swirls) and the mouse cursor pops up...i can move the pointer but nothing else ever loads......i try to reinstall but it still hangs on the same package.....i reinstall again remove the apparenly offending packages from the update list...but it just hangs on another one......

any help would be great

I hope i was specific enough.

Drewbert

---

### Post by drewbert on 2006-07-26
oh yeah...i'm running (trying to run) 6.06....

---

### Post by philippe_carlo on 2006-07-26
Can you open a terminal and try

```
sudo apt-get update -f
```

---

### Post by drewbert on 2006-07-26
I'll try that when i get home...i'm not at that machine right now

---

### Post by WaxwingSlain on 2007-12-11
I'm having the exact same problem.  

My fresh installation of Ubuntu Studio 7.1.0 goes smoothly.  I am presented with a list of 140 updates as soon as I boot up.  At this point, everything seems to be working fine.

I start the update manager, all the files are downloaded, then it starts processing the updates.  Somewhere along the line, everything locks up and I can't move the mouse or use the keyboard.  Everything is stopped.  The only thing I can do is a hard reset of the computer, but now it won't boot into the system.  The only choice at this point seems to be another fresh install.

The third time this happened, I decided to watch the system throughout the updating process.  Things were working well, but I started noticing "parsing errors" when it was doing the cupsys updates.  It seemed to get past some errors, but then a series of parsing errors occurs and everything locks up tight again.

The last thing it says before the lockup is "unpacking replacement cupsys".

---

