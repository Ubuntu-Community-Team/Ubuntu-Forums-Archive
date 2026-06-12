---
title: "Desktop never clears dialog boxes"
date: 2013-10-24
forum: Desktop Environments
---

### Post by Roy_Finklea on 2013-10-24
On boot the login screen has my correct desktop background after login the desktop background turns to black and any dialog boxes that open never close or refresh they just tile one on top of the other.  Opening any other application works normaly but when the application closes the last screen tiles on top of the desktop.  I had a problem with nvidia drivers and am currently running 304.88 kernel 3.02.55 64 bit 1204 lts.  Not sure what else to list for help with this.

---

### Post by hansdown on 2013-10-24
Welcome to the forum, Roy_Finklea.

Which nvidia card do you have, and where did you go to get the drivers?

---

### Post by Roy_Finklea on 2013-10-24
GeForce 8800 GT/PCIe/SSE2   I got the drivers from kernel nvidia system settings additional drivers and activated the recomended driver.  I have been using this driver for a while but after an update when desktop loaded I had " can not write bytes: broken pipe"  error followed another fix and went back to earlier driver.  That didn't work and I finally fixed API mismatch error but still have the issue.  Cinamon desktop seems to be fine but gnome classic which I have always used is exibiting the problem.  I am in Cionamon now and have no problem.  Is there a reset for gnome?

---

### Post by hansdown on 2013-10-25
I see that some of the recommende linux drivers are

2.80
2.85.03
2,85.09
2.90.10
2.95.20

Will any of these give better experience?

---

### Post by Roy_Finklea on 2013-10-27
:p reinstalling gnome3 solved the problem as it was only occuring in Gnome desktop.  Thanks for the replys.

---

### Post by hansdown on 2013-10-27
Glad you fixed it,Roy_Finklea. 

Good work.

---

