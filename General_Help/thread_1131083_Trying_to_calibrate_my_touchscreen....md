---
title: "Trying to calibrate my touchscreen..."
date: 2009-04-20
forum: General Help
---

### Post by bryceowen on 2009-04-20
I have a Lifebook P1120 that has a touchscreen connected by USB. Now, I've read the very complete writeup by Simon Funk ([http://sifter.org/~simon/journal/20030911.html](http://sifter.org/~simon/journal/20030911.html)) and even tried his joytouch fix. I even tried contacting him directly when joytouch did nothing. He says he wrote joytouch because his system was seeing the touchscreen as a joystick. How can I find out how mine is being recognized? When I run lsusb, I get two devices:

Bus 001 Device 002: ID 0430:0508 Sun Microsystems, Inc.
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I'm guessing the first one (Device 002) is the touch screen, but I could really use some more information. What should I do to find out where this device is setup? It works in that I can touch the screen and the cursor will move, but it isn't calibrated at all and I need to set some offsets...

---

