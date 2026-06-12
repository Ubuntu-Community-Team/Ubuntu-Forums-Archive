---
title: "Feisty graphics problem"
date: 2007-04-21
forum: Desktop Environments
---

### Post by anubis2814 on 2007-04-21
I upgraded to Feisty and LOVE it, however due to it's being so new, my Ndiva driver was listed as limited capacity and its moved the screen position.  So I removed it, but before hand I had turned on the screen visuals(can't remember what they are called, they make desktop items wiggle when you move the mouse).  After removing it, it told me to restart.  After the start up music played the screen went black and then white.  There was a mouse cursor and that was all on a white screen.  I tried restarting it in the various safe mode but nothing worked.  I am wondering if I can do something in the root terminal (recovery mode) to repair my graphics driver.  I am not very good with linux terminals so please help me out, don't feel like reinstalling everything.

---

### Post by taurus on 2007-04-22
The wiggle thing is probably either compiz or beryl.  However, boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

