---
title: "kdetv prob/no proper sound"
date: 2005-05-27
forum: Desktop Environments
---

### Post by @jens on 2005-05-27
Hello

I just installed Kubunto for my daughter. All is running fine, but:
Pinnacle PCTV card (mono, no radio), SB Live card/kdetv.
Picture is pretty fine, all 5 channels are working, but audio delivers only noise, no sound.
I googled ad nauseam. Many users have the problem but it seems that there is no solution out there. BTW there is no "PAL-i" available in the channel search menu. Anyone out there who could manage to watch TV with this hardware/software?

Many thanks in advance!
@jens

---

### Post by @jens on 2005-06-06
$ sudo gedit /etc/modprobe.d/tv
options tda9887 pal=i

...did the trick. Picture and sound are pretty good now.
regards,
Jens

---

