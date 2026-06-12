---
title: "screen rez problem"
date: 2007-02-13
forum: Desktop Environments
---

### Post by virtualsnyper on 2007-02-13
hey a;;. I wanna say thx for helping me out. I love that linux has a tight community :P. I was wondering if anyone would know why I couldn't get my screen resolution above 1024...I have a 7900gs, im running edgy x64. Nvidia drivers installed....what gives?

---

### Post by drdnl on 2007-02-13
Hi there,

google your monitor and write down (or simply note) the horizontal and vertical refresh. open a terminal and type 

sudo gedit /etc/X11/xorg.conf

look for the horizontal and vertical refresh and replace with the values you noted. In my case its 50-160 and 30-130 (from memory). Save.

Now restart your xorg (save anything else as well) with ctrl+alt+backspace

Less hastily typed information can be found here: [www.ubuntuguide.org](www.ubuntuguide.org) :)

Good luck and hang in there, i switched 7 months ago and don't miss windows a tiny little bit.

---

