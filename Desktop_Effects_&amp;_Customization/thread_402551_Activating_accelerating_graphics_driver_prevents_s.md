---
title: "Activating accelerating graphics driver prevents startup"
date: 2007-04-05
forum: Desktop Effects &amp; Customization
---

### Post by MyDearWatson on 2007-04-05
Hey all, new to ubuntu, and even though this is more of a driver issue, my ultimate goal is to enable desktop effects, so I figured this was a logical place to post.

Anyway, when I go to enable desktop effects, it warns me that I need to install Nvidia's accelerated graphics driver.  When I do that and reboot, I get an error (can't remember exactly what it said, but the xserver refuses to start).  There's probably a command to disable the drivers and start it up again, but rather than being smart and realising that, I've reinstalled about 6 times now.

I have tried getting the drivers through the terminal, I've tried the latest version of envy (tells me that my OS doesn't support it), and I've tried just about everything I could think of.

It could also be useful to know that I used Wubi to install, if that affects the drivers.  Is there any way to get the effects to work without causing Ubuntu to refuse to boot?

EDIT:  Specs-

AMD Athlon X2 5200+
Nvidia Geforce 6600gt
1024MB RAM
SB Audigy (which also doesn't work right with ubuntu)

---

### Post by xopher on 2007-04-06
What's Wubi?

Anyway, we need the exact error to tell you what really is wrong :)

Now, the nvidia-glx drivers for edgy are outdated, they're not 9x.xx series, ergo they won't work with desktop-effects without XGL, and this we don't want.

So if your not on feisty, you'll need to get the official installer for the 97.55 drivers from nvidia.com, and install them.

Now, how to fix xorg.conf to be able to graphically login again?
```
sudo nano /etc/X11/xorg.conf
```

Edit nvidia to nv in the device driver section, save, and issue ```
sudo invoke-rc.d gdm restart
``` to get to X.

(Get back to the terminal with CTRL+ALT+F1...F6, and the back to graphical: CTRL+ALT+F7..)

---

