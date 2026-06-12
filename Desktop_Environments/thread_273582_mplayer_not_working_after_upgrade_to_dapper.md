---
title: "mplayer not working after upgrade to dapper"
date: 2006-10-08
forum: Desktop Environments
---

### Post by maciu on 2006-10-08
Hi all,

I have upgrade my brezzy to dapper long time ago, and since then i cant get the mplayer to work again. When i try to open a movie in mplayer a little window pops-up and dissapears at exactly thensame time so there is no error info or anything i could see that caused the error. I tried removing mplayer with apt-get and re-installing it but that didnt help either... :confused:

---

### Post by elettronicha on 2006-10-08
Do you mean mplayer crashes and you aren't able to watch to the video? Try to open a terminal, to launch mplayer with the command 'gmplayer' and report the message you get.

---

### Post by maciu on 2006-10-08
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


xscreensaver_disable: Could not find XScreenSaver window.
Cannot load font: /home/maciu/subfont.ttf
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
[skin] file ( /usr/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).


thats the output

---

### Post by elettronicha on 2006-10-08
Did you install the package 'mplayer-skins'?

---

### Post by maciu on 2006-10-09
yes i do have the skins package...

---

