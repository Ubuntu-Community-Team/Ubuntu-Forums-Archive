---
title: "Starting the desktop in 6.06 server (LAMP)"
date: 2008-04-13
forum: Desktop Environments
---

### Post by liche24 on 2008-04-13
I've tried many options from forums to fix my problem, with no success.  I have 6.06 server edition loaded and cannot get the desktop to start.  I've done apt-get install ubuntu-desktop xserver-xorg, and the aptitude as well.  They seem to load, but when I check my /etc/init.d for gdm, nothing.  When I try startx, my screen will blink a couple of times, and nothing.  When my systems boots up, i use usplash and get a nice gui of my boot process.  Has anyone solved my problem?  I've been working on this for 2 weeks now, with no success from any forum.  I Thank you in advance for any help.

---

### Post by warp99 on 2008-04-13
You need to install a desktop kernel since the server kernel does not include all the modules needed for a ubuntu-desktop install. All of your server applications will still run on a desktop kernel:

```
sudo apt-get install linux-image-2.6.15-51-386
```

Use 'linux-image-2.6.15-51-686' for a Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV with SMP support or use 'linux-image-2.6.15-51-amd64-generic' if your running on the x86_64 version. Once that's installed boot to the new kernel, then run:
```
sudo apt-get install ubuntu-desktop
```

---

