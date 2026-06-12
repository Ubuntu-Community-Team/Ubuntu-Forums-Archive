---
title: "DPMS not working"
date: 2005-05-22
forum: Desktop Environments
---

### Post by ioliver on 2005-05-22
Anyone got any ideas on how to troubleshoot DPMS problems?

My monitor is DPMS capable.
I have Option "DPMS" in the monitor section of xorg.conf
"xset -q" reports - 
DPMS is Enabled

If I do -
xset dpms force off
the monitor remains on. :-(

However, if I do "xset -q" again (via desktop sharing) I can see -
Monitor is Off
in the ouput.

So xset thinks it's turning my monitor off, but my monitor disagrees. The same monitor works fine on a different machine.

Anyone know anything else I can tweak/change/try?

Thanks

Ian

---

### Post by ioliver on 2005-05-24
I tried all sorts of stuff, googled for ages, and finally stuck in a different video card.

It now works, but doesn't help in the cases where someone doesn't want to swap video card!

Ian

---

### Post by Burgundavia on 2005-05-24
Can you file about this. It should just work.

bugzilla.ubuntu.com

Corey

---

### Post by ioliver on 2005-06-09
It was a rather old PowerVR card. Still worth filing?
Ian

---

