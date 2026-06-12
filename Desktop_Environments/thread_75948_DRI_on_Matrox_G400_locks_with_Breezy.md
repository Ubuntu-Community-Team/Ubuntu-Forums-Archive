---
title: "DRI on Matrox G400 locks with Breezy"
date: 2005-10-14
forum: Desktop Environments
---

### Post by ioliver on 2005-10-14
I have been using an AMD64 with the 386 kernel and Hoary for ages with no problems. I just upgraded to Breezy and any attempt at graphics on the card causes the system to lock solid(1) - even glxgears or a screen saver takes it out.

Commenting out the DRI load line in xorg.conf fixes it. 

I tried a totally clean Breezy install to a spare partition and this behaves exactly the same.

Common problem?
Suggestions?

Regards

Ian
(1) Sometimes the power button will shutdown the machine, sometimes I can still ping the machine, as often as not there is no sign of life.

---

### Post by ioliver on 2005-10-17
<bump>

So I guess this one needs to go to bugzilla?

Ian

---

### Post by ioliver on 2005-10-17
Cancel that, it's already there - [http://bugzilla.ubuntu.com/show_bug.cgi?id=15036](http://bugzilla.ubuntu.com/show_bug.cgi?id=15036)

Though my lockups are on an AMD64, which should have SSE/SSE2

Ian

---

