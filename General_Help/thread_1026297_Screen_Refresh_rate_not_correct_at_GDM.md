---
title: "Screen Refresh rate not correct at GDM"
date: 2008-12-31
forum: General Help
---

### Post by Prodigious Penguin on 2008-12-31
Hi, I just installed Intrepid on a desktop with a Triplex Xabre Pro graphics card, although I suspect the actual problem is with my Cornea CT1702T LCD.  I can see usplash all fine and dandy, but get an "Out of Range" message on my LCD when GDM comes up.  I plugged in a CRT an confirmed that it's pushing 1280x1024 @ 60Hz, a mode seemingly incompatible with the LCD.  When I upped the refresh rate to 85Hz, the LCD started working just fine.  However, I can't figure out how to get GDM or the system as a whole to default the refresh rate to 85Hz.

And here's the output of my Xorg.0.log file in case anyone needs that:  [http://paste.ubuntu.com/96586/](http://paste.ubuntu.com/96586/)

Thanks!

---

### Post by Prodigious Penguin on 2009-01-01
I also tried SSHing in and using xrandr, but got a "cannot connect to display" type message.

---

