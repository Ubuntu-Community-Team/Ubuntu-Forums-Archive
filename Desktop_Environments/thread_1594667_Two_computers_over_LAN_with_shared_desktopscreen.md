---
title: "Two computers over LAN with shared desktop/screen"
date: 2010-10-12
forum: Desktop Environments
---

### Post by gohatto on 2010-10-12
Hi guys!

I was thinking about using my laptop as a secondary screen for my desktop Ubuntu. To describe the problem:

- One desktop computer with monitor - Ubuntu on the board, nVidia GPU
- One laptop - Ubuntu on the board, ATI GPU
- Both computers are connected over the LAN

I would like to achieve something like you got when you attach two (or more) monitors to single computer - the desktop is extended to match the space created by the two monitors.

I've tried xinerama, but it's configuration is so unpleasant, that I didn't manage to make it run (black screen with X on the middle on the laptop).

I was thinking - if the desktop "spanning" (to create ONE, wider, desktop) is impossible, maybe there is some way of accessing different dekstop on one computer, so:

- The computer is running GNOME with 2 virtual desktops (I'm talking about this desktop switcher widget, by default on the lower right corner)
- The computer is using desktop no 1
- The laptop connects to the host computer and uses desktop no 2

By default VNC allows to connect to the SAME desktop, not to another one, and I would like to achieve that I've got the same environment on both computers.

I would be very greatful for any advice you can give.

Regards.

---

