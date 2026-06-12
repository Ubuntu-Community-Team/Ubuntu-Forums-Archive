---
title: "Xubuntu crashing during install"
date: 2006-07-05
forum: Desktop Environments
---

### Post by oscartheduck on 2006-07-05
Yesterday evening I tried to install Xubuntu 6.06 on my home desktop. It is a pentium 3 machine with 128 megs of RAM, shared video from intel onboard.

It booted fine into the live CD. I clicked the install option on the desktop and the installer started. It seemed laggy, very laggy indeed. I had to click "Forward" a few times on some of the screens. Other live CDs, such as Knoppix, have no issues running (albeit somewhat slowly) on this machine. But in the case of Xubuntu, I was experiencing things like the mouse pointer not following the mouse movements properly, instead being jerky.

Initially, it crashed on the "select a time zone" screen. I clicked on the map, and after it had zoomed in then the installer halted and locked up the mouse pointer. I left it alone for a few minutes but it didn't come back alive and didn't release the mouse pointer.

I tried again, this time selecting a city from the drop down list. It worked fine, though it was still laggy. On the partitioning screen, I clicked the advanced or custom button, I forget which it is, but I needed to do some custom paritioning. It went to the next screen which warned me about partitioning, and then locked up completely again.  Every time I try it, it locks up at this screen.

I tried it with the "safe graphics mode" option, and it looked like it could have worked. It was much much smoother. However, the screen resolution was resized, but the resolution of the installer's windows was not, so that I had enormous windows inside a tiny screen with no scroll bar or anything similar to allow me to navigate. So while I could sit there hitting enter and hoping for the best, I couldn't actually see what buttons were highlighted when I was hitting enter. As such, I wasn't able to get past the choose time zone screen. I clicked on a city and that worked fine without locking up the computer, but I couldn't see the drop down menu or see the bottom of the window to highlight "forward".

Is this a known issue?

---

### Post by gotfoo on 2006-07-05
You may want to try the **[Alternate install CD]("http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/")** instead which is for systems with less than 192MB of RAM. 

The LiveCd is sucking up all of the available 128MB of RAM which is causing the system to perform in slow-motion.

---

