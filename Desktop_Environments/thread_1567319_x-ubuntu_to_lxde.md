---
title: "x-ubuntu to lxde"
date: 2010-09-03
forum: Desktop Environments
---

### Post by pdc124 on 2010-09-03
ive got a machine running x-ubuntu and have install lxde , but i dont get an lxde option in the startup - xfce, gnome, terminal etc etc  , but not lxde. 
So what do i need to tweak  ?

---

### Post by Silent Warrior on 2010-09-03
What packages did you install, exactly? You might need the two lxsession-packages. Safest bet is of course just installing from a Lubuntu CD. I can guarantee you, from personal experience, that you won't have to tweak anything to get LXDE in the list of available sessions. Hell, I didn't even have to do that when I tried ArchLinux. Did you reboot between installing LXDE and trying to log into it, by the way?
Otherwise, you could also try the lubuntu-desktop metapackage. Manually picking every package that starts with 'lx' is also something to consider.
Oh yeah, lxdm isn't exactly necessary, and might have a somewhat scary prompt show up. It worked just fine for me every time I used it, but gdm will still do the trick.

---

