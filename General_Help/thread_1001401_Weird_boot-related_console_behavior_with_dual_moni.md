---
title: "Weird boot-related console behavior with dual monitors"
date: 2008-12-03
forum: General Help
---

### Post by mskoh52 on 2008-12-03
Hi. I've searched just about everywhere to get a handle on this problem I'm having but I'm pretty much stuck. I'm using a laptop with an external monitor. The virtual console (Ctrl+Alt+F1-F6) only appears on my external monitor, which is a problem if I ever want to use it when the monitor isn't plugged in.

My setup:
Laptop (HP tx2120) with an external monitor; nVidia Geforce go 6150. For dual-monitor stuff, using TwinView at 2720 x 900 resolution (1280 + 1440 x 900). I have two xorg.conf files that I swap between for when I have the monitor unplugged and when its plugged in (see attachment). In the dual setup, I set my external monitor as the primary monitor (i.e. TwinViewXineramaInfoOrder set to CRT-0)

While the computer is booting up, the bootup messages get displayed to both screens perfectly fine. However as soon as I log in, all console output only goes to the external monitor. So when I hit Ctrl+Alt+F1 it only goes to the external, and when I shut down or reboot the computer, all the messages are only displayed on the external.

Also, even if I am using the single-monitor xorg.conf with the external monitor plugged in, I get the same behavior. During boot, everything is displayed on both screens, after bootup is finished, only external monitor gets console output.

So obviously the problem isn't directly related to X. This makes me think that for some reason, whatever process it is that sets up the consoles tty1-tty6 during bootup is only using the external monitor. Does anyone know the point during the whole boot process that the ttys are set up? What do I need to modify so that it uses either both monitors or just the laptop internal monitor?

Thanks in advance.

---

