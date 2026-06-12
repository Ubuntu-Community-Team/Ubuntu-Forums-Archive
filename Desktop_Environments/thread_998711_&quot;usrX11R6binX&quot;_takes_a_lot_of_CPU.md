---
title: "&quot;/usr/X11R6/bin/X&quot; takes a lot of CPU"
date: 2008-12-01
forum: Desktop Environments
---

### Post by aleck on 2008-12-01
hi, all
I'm using ubuntu 8.10 on IBM T61p, I found my system is slow even at idle time. Can anyone help me on this ? Thanks in advance.

Detail description:

After login, I close all the windows except for a terminal and a system monitor, do nothing, I found the CPU is always busy. The two CPUs becomes busy alternatively (I think this is due to the system dispatch), but the sum of both CPU usage is stable at about 60%.
From the figure, we can see, the curves in system monitor is quite abnormal.

"ps -aux"
I found "/usr/X11R6/bin/X" takes a lot of CPU (nearly 60%), 
I checked my desktop (integrated graphic card), it's also using ubuntu 8.10, the ratio is about 2% even open highest desktop effect. So I guess there's some wrong with "/usr/X11R6/bin/X" or my configuration.

"top"
I also tried "top", It seems that "xorg" takes most of the CPU time, as shown in the terminal.
If I close the system monitor, the cpu usage of "xorg" drop to 4%, but I still feel the system very slow.

It doesn't matter which level of desktop effect I'm using, the problems occurs all the time.

Pictures are attached.
ubuntu-cpu-chart2.png is when no desktop effect is on.
top-no-desktop-effect.png: output of top command

* my laptop:
CPU Intel Core Duo T7700
Memory 4GB
Graphic Card: 256MB nVIDIA Quadro FX 570M

* my desktop
CPU Intel Core Duo E7200
Memory 2GB
Graphic Card: Intel G31/33 integrated graphic card

I hope someone can help me on this, or give some suggestion.
I've searched on the web for a long time, but haven't found much useful. 
Thanks very very much.

---

### Post by edmondt on 2008-12-07
I have the same problem...
CPU 89% /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

---

### Post by edmondt on 2008-12-09
Anyone?

---

### Post by sdennie on 2008-12-10
This sounds like the known bug with gnome-system-monitor where the monitor itself takes huge amounts of CPU.  Rather than using gnome-system-monitor, use top or htop in a terminal to get more accurate results.

---

