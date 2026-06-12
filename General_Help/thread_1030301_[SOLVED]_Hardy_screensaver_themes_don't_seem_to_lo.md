---
title: "[SOLVED] Hardy: screensaver themes don't seem to load"
date: 2009-01-04
forum: General Help
---

### Post by heindsight on 2009-01-04
I'm having some difficulty with gnome-screensaver on my laptop running Hardy. 

Regardless of which screensaver theme I select, when the sceensaver is activated (either through locking the screen or when the machine goes idle) I just get a black screen - the screensaver theme doesn't seem to load.

In the screensaver dialog, the themes display correctly in the small preview window and clicking the 'preview' button correctly runs the screensaver themes in fullscreen mode.

The graphics card is an Intel 82852/855GM Integrated Graphics Device (rev 02) using the i810 driver (the newer intel driver is rather buggy) and I have all desktop effects disabled.

At first I thought the problem may be due to some misconfiguration somewhere in my user account, so I created a brand new user and when log in with that account the same thing happens.

Of course this isn't a serious issue, but I miss being able to see a slideshow of my photos when the machine is idle...

Anyone got any ideas?

---

### Post by heindsight on 2009-01-04
I checked launchpad before posting this thread but I couldn't find anything related to this. I checked again now and found [https://bugs.launchpad.net/bugs/60394](https://bugs.launchpad.net/bugs/60394)

---

### Post by heindsight on 2009-01-05
I've found the problem. It turns out that HAL is confused - it thinks I'm running on battery when I'm actually running on AC. See [https://bugs.launchpad.net/bugs/201318](https://bugs.launchpad.net/bugs/201318)

This is causing gnome-screensaver to only blank the screen rather than displaying my chosen screensaver (presumably in an attempt to save power). I can fix the problem by just unplugging and reconnecting the power cable.

---

