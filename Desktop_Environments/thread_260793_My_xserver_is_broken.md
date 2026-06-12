---
title: "My xserver is broken"
date: 2006-09-19
forum: Desktop Environments
---

### Post by martintfd on 2006-09-19
Hello,

I did an update this morning and now my xserver is broken, I have an nvidea graphics card, how do I fix this? it's very annyoing as I have work to do!

Martin

---

### Post by whizbaby on 2006-09-19
What driver is set for your card in /etc/X11/xorg.conf, *nv* or *nvidia*?
If *nvidia*, change to *nv*, save and
sudo /etc/init.d/gdm restart
You should be able to work and fix the nvidia-thing later.
If this doesn't help at all it's time to reinstall the driver or go back to the older version of xorg (**man apt-get** will tell you how to select a specific version)

---

### Post by martintfd on 2006-09-19
That's got it back to a state where I can work, thanks for your rapid reply I can sort it out properly later...

Thanks again

Martin

---

