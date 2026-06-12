---
title: "Unity won't load after flrgx driver install"
date: 2011-10-20
forum: Desktop Environments
---

### Post by nikkkko on 2011-10-20
Hi,

I had all working great on a virgin 11.10 install except I had no sound over hdmi. I chose to install the additional ati driver, flrgx, and that fixed the problem except that the display then showed a black frame all around the screen.  

Rather than play around with the display, I decided to run an audio cable to the screen and revert back to the standard Ubuntu display driver but.... now Unity doesn't run on boot.

I've reinstalled xserver and unity with no joy.  

Any suggestions welcome

Nick

---

### Post by nikkkko on 2011-10-20
OK, I fixed this by running :

```
sudo apt-get install --reinstall libgl1-mesa-glx:amd64 libgl1-mesa-glx:i386
dpkg-reconfigure xserver-xorg

```

Turns out that flrgx is a dog and leaves mess all over the place.

---

