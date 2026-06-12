---
title: "KDE-light or XFCE?"
date: 2005-09-14
forum: Desktop Environments
---

### Post by Terracotta on 2005-09-14
At the moment (due to a sudo apt-get upgrade, what's wrong with those devs??, every time when I do an upgrade there's always something broken, this time it's the nvidia-drivers or xorg, can't get loginscreen anymore, but that's off-topic) my ubuntu install is down, and I'm about to install a linux distro on an old computer (duron 800), I tried Kubuntu, but well, waiting five minutes for a window to pop up isn't workable, so I was wondering if KDE-light is in the repository list (I can't check it myself)? and if so how I can get it (or xfce) to work without installing ubuntu-desktop or kubuntu-desktop (just a server install and from there on). Can anyone help me with this?

---

### Post by gingermark on 2005-09-14
KDE-Light doesn't appear to be in the repositories. As far as XFCE, sudo apt-get install xfce (or xfce4) should do the trick. I'm not up on server installs, but I reckon it should work. You definitely won't need any of the other desktop metapackages. I run XFCE under KDM, but I think it does come with it's own desktop manager, so you should be fine.

If it doesn't work though, sudo apt-get install gdm or kdm would probablt do the trick. I've never done this myself though, so although I'm confident that this is correct, you might want to wait for someone else who is certain.

---

