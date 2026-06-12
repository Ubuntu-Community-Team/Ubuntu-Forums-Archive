---
title: "krfb (Desktop Sharing) is terribly slow and pixelated"
date: 2009-07-08
forum: Desktop Environments
---

### Post by prshah on 2009-07-08
Hello,

A bit of background: I have recently installed KDE4.1 "on top" of my existing Ubuntu 8.10 installation. In Gnome, I was able to use Desktop Sharing ( vino-server? ) without any problems.

In KDE, I understand the equivalent is krfb.

However, when I connect to my machine running krfb, the display is highly pixelated (to the point of being unreadable) as well as extremely slow, to the point of being unusable (ie, the desktop loads, and not much else; no mouse cursor, movement, etc etc). Neither machine jams / freezes, the keyboard is responsive for the remote machine, but keypresses go through only after a delay of about 1-2 seconds for *each* keypress.

Am I missing something in configuring krfb? I have set it to accept uninvited connections, and am able to connect to it, but not usably. It's not a connection or system problem, logging into Gnome lets me use Desktop Sharing fine.

Failing a fix for krfb, can anyone recommend an alternative (VNC compatible)? I'm happy with gnome's vino-server, any suggestions how to start it up in KDE?

Any experiences with x11vnc; tightvnc; etc? 

Thanks in advance

---

### Post by Zorael on 2009-07-08
Yeah, krfb is garbage. :<
```
[Tue Jul 7 2009] [20:08:40] <Zorael^2>	Is krfb broken? Mine sits at 25% when idle (noone connected, just started it), and produces 6500+ lines of strace output a second
[Tue Jul 7 2009] [20:09:03] <kyron>	Zorael^2: nah, krfb has always been a hog
[Tue Jul 7 2009] [20:09:16] <kyron>	oh...and yes, its also always been broken ;)
[Tue Jul 7 2009] [20:09:18] <Zorael^2>	kyron: Yeah, but 6.5k a second? :(
[Tue Jul 7 2009] [20:09:19] <Zorael^2>	eheh
[Tue Jul 7 2009] [20:09:49] <kyron>	Zorael^2: it's probably polling like mad
[Tue Jul 7 2009] [20:10:09] <Zorael^2>	kyron: 9928  20:06:16.001473 poll([{fd=3, events=POLLIN}, {fd=8, events=POLLIN}, {fd=9, events=POLLIN}, {fd=7, events=POLLIN}, {fd=11, events=POLLIN}], 5, 0) = 0 (Timeout)
[Tue Jul 7 2009] [20:10:17] <Zorael^2>	with some reads here and there, and selects
[Tue Jul 7 2009] [20:10:41] <kyron>	yep, horrible coding practice...not using software interrupts
```
I use x11vnc. I can't say how it compares against vino, but it does the trick marvellously.

---

