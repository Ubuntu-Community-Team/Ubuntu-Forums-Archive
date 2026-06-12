---
title: "Video Games Crash Randomly"
date: 2009-06-12
forum: Gaming &amp; Leisure
---

### Post by amazurenko on 2009-06-12
Hello,

I have an issue where video games (Sauerbraten and Urban Terror) crash randomly. The window resizes from full screen to being a window on my desktop. The game continues playing (graphics in the new window + sound), but my input does nothing, and I have to go ctrl-alt-F1 and use the commandline to kill the process. Since identical errors happen for 2 games, it cannot be their fault. 

I am using a Thinkpad T61 with Nvidia quadro 140M, and appropriate driver installed.

Thank you,

amazurenko

---

### Post by matthewjames on 2009-06-13
Could you please port more information about your system? What is your graphics card etc. Also which version of ubuntu are you using, and is it 32/64 bit?

---

### Post by Sealbhach on 2009-06-13
> **amazurenko said:**
> Hello,

I have an issue where video games (Sauerbraten and Urban Terror) crash randomly. The window resizes from full screen to being a window on my desktop. The game continues playing (graphics in the new window + sound), but my input does nothing, and I have to go ctrl-alt-F1 and use the commandline to kill the process. Since identical errors happen for 2 games, it cannot be their fault. 

I am using a Thinkpad T61 with Nvidia quadro 140M, and appropriate driver installed.

Thank you,

amazurenko

The exact same thing happens to me in Sauerbraten. I use a 64-bit system, and I always select Openbox as my window manager before playing, but it still happens. Not often, about once every three hours of play.

.

---

### Post by amazurenko on 2009-06-13
Specifications: Lenovo Thinkpad T61, 3gb ram, core 2 duo 2.4GHz. Ubuntu 9.04, 64bit, Gnome. Does any of this help?

---

### Post by matthewjames on 2009-06-13
> **amazurenko said:**
> Specifications: Lenovo Thinkpad T61, 3gb ram, core 2 duo 2.4GHz. Ubuntu 9.04, 64bit, Gnome. Does any of this help?

I need to know the type of graphics card you have. Once you find that out, if you know what driver your using for it please list it.

---

### Post by matthewjames on 2009-06-13
> **Sealbhach said:**
> The exact same thing happens to me in Sauerbraten. I use a 64-bit system, and I always select Openbox as my window manager before playing, but it still happens. Not often, about once every three hours of play.

.

Which graphics driver are you using? If you are using ubuntu 9.04 and a nvidia card; open hardware drivers in System: Administration. After it scans you should see two options for graphics select and install "NVIDIA Accelerated graphics driver (version 180).

After doing this, restart, then go to system, administration, nvidia x server settings. Do what the pop up window says to. To restart the x server launch a terminal and type:

```
sudo -s
/etc/init.d/gdm restart
```

Your system might get stuck at reloading, if so just hit ctrl-alt-delete and let your pc restart. Should work :)

---

### Post by Sealbhach on 2009-06-13
Thanks. I've got the Nvidia 8400 card and I've been using the 180.44 driver but it still crashes occasionally.

.

---

### Post by wubiubiubi on 2009-06-14
Hi,
  I think I know the problem, i had the same one. the reason for the minimization is that the screensaver is trying to come on. for some reason, when it comes on, the screen minimizes and all input is stalled. try setting it so the screensaver doesn't come on for 10 hours, see if that works.

---

### Post by lowpine on 2009-10-04
I'm having the same problem, it happens every 5 min or so..... I'll try the screensaver options.  thanks wubiubiubi.  these forums are great

---

