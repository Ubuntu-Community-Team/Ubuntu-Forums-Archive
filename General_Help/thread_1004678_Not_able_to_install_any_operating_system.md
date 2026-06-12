---
title: "Not able to install any operating system"
date: 2008-12-07
forum: General Help
---

### Post by lolhello on 2008-12-07
Hi, I installed Ubuntu Server Edition 32 bit on my Dell desktop which is about eight years old, and now I'm trying to install Ubuntu 8.10 Desktop or Windows XP. Every time I run the disk, the screen goes blank.  It wasn't like this before, and I'm a complete noob in Linux and Ubuntu. Thanks for helping :KS

---

### Post by taurus on 2008-12-07
8 years old Dell!  Do you know the spec of that machine?

---

### Post by lolhello on 2008-12-07
Well I don't want to look it up, but I guess I can if I have to.. Pretty sure it's the server edition that's messing me up. :popcorn:

Intel Pentium 4 @ 1.88 Ghz
512 mb Ram
Running Ubuntu 8.10 Server Edition 32 bit ATM

---

### Post by taurus on 2008-12-07
You already have Ubuntu server running on that machine and now you want the desktop.  No need to reinstall.  Just install the ubuntu-desktop package.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by lolhello on 2008-12-07
Wow thanks! Didn't know I could get the solution so fast. :D

---

