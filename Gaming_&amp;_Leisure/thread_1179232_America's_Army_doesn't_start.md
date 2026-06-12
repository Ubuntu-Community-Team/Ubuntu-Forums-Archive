---
title: "America's Army doesn't start"
date: 2009-06-05
forum: Gaming &amp; Leisure
---

### Post by walpoles93 on 2009-06-05
Hi, 

Iv'e been trying for a while now but no matter what I do, I can't get America's Army to run.  I'm running Ubuntu 9.04 on a Sony Vaio VGN-NR21M laptop.

Basically, I install it then find the launcher in 'Other'(strange).  When I click on it, absolutely nothing happens.  It doesn't even attempt to load anything.

Does anyone have a solution?
Thanks

---

### Post by JonnyM on 2009-06-06
Try using 2.5 Assist...

---

### Post by walpoles93 on 2009-06-06
Hi,

Thanks for the reply.  I've downloaded the AA Assist tarball and extracted it.  I get the AA Assist executable but when I click on it the screen comes for a moment and then disappears again.

What could be the problem?

---

### Post by walpoles93 on 2009-06-06
Don't worry I've sorted that out now.  Turns out you have to run it as root.:p

---

### Post by goran.26 on 2009-08-03
I have some problems with this too. I installed 25Assist, and it worked fine. But once I started AA my screen goes black and states "out of range 81.2kHz/65Hz". I then have to restart the xserver. 
Also I do not know how to start 25Assist again... There is no entries in the menus or on the desktop for it.

Edit: Fixed the out of range error by adding these lines to the screen section in xorg.conf:
Option "ModeValidation" "NoXServerModes"
Option "ModeValidation" "DoubleScanPriority"

---

