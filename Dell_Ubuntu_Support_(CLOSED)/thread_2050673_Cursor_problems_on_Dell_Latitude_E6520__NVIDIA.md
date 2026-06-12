---
title: "Cursor problems on Dell Latitude E6520 / NVIDIA"
date: 2012-08-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by McGuinness on 2012-08-31
Hi folks,

I've checked this forum but I did not find anything which could help me in solving my problem, so I thought I will open a new thread. My apologies, if I missed something.

Since I upgraded from 11.10 to 12.04, I have a strange problem with Ubuntu on my Dell Latitude E6520.

In the office I use a docking station and a second screen which is connected via DVI. Everything works fine so far. However, as soon as I un-dock the notebook and either plug another screen via VGA or even do not plug anything else, the mouse cursor starts jumping up and down if I move the mouse in any direction (it looks like I have three or more cursors at the same time on the screen when I move the mouse). It does not matter if I use an USB mouse or if I use the touchpad.

According to the NVIDIA X Server Settings this notebook uses an NVIDIA NVS 4200M graphic card. Furthermore I am using Ubuntu 12.04 LTS with Gnome 3.

Does anybody have the same problem or a clue what might causes this?

Cheers
McG

---

### Post by Colo993 on 2012-09-04
McGuinness,

I have a Dell Latitude E6510 with an Nvidia chipset running 12.04 and Gnome 3.  I also have a Dell docking station with a monitor plugged in the DVI port on the docking station.  I haven't had the exact problem you are having with your mouse when you undock but I do have problems losing the mouse cursor once undocked.  To cure these problems, I have an xorg.conf for when I docked and another for when I'm undocked and using only the laptop screen.  I copy the files over the running xorg.conf, hit CTRL-ALT-F1 stop and then restart GUI.

I have tried the latest Nvidia drivers but keep finding issues (suspend doesn't work) and have had the best luck with the 295.59 drivers.

Colo993

---

