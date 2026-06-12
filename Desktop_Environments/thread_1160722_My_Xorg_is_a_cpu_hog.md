---
title: "My Xorg is a cpu hog"
date: 2009-05-15
forum: Desktop Environments
---

### Post by draynes on 2009-05-15
I have a new install of 8.04 LTS and tried an install of 9.04 on an old AMD K6-500 box.  Both installs showed low cpu usage with Conky and htop until I started adding software and updates.  I have turned off everything possible in my startup list and sessions and I still see 30-35% cpu usage by Xorg while the computer is just sitting there doing nothing.

Htop shows this for Xorg:

/usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm:0.Xauth -nolisten tcp vt7

Before I try tweaking any of these parameters, can anyone shed some light on what might have changed with my X server while updating and adding some new packages?

I don't know if the culprit is X, gdm, or something else.  ???

ETA: All my other installs of Ubuntu of all versions on different boxes didn't do this.  I've used various Ubuntu distros for several years now on a half dozen boxes.

Another clue:  moving the mouse pointer around in a circle bumps the cpu usage up to 80%.

DISREGARD - BLEW THIS DISTRO AWAY AND INSTALLED XUBUNTU 9.04.

---

### Post by Endolith on 2009-06-17
I have this, too.  Killing vino-server seems to fix it.

---

