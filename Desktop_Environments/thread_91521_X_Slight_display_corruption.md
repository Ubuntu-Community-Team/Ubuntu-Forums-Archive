---
title: "X: Slight display corruption"
date: 2005-11-17
forum: Desktop Environments
---

### Post by lcg on 2005-11-17
Hello,

I have an Ubuntu box where X is acting up. Just a little, but it is annoying:

Every time the system starts (or X restarts after logging off), it looks as if the screen area is shifted about 20 pixels to the right. Those pixels are cut off, but they appear on the left side of the display. You can move the mouse cursor to the right edge of the screen, which causes the cursor to reappear in the few collumns at the left hand side. :( Additionally, the cursor looks scrambled when it is in this area but looks fine once you move it back into the "normal" part of the screen.
The problem can be cured by either a) switching the display off and back on, b) switching to one of the TTYs and back or c) resetting the display. But that is only a solution until the next logout or shutdown/reboot.

Now for some information about the config: a (mostly) stock Ubuntu 5.10, using an ATI Radeon 9000 with the xorg driver (not fglrx) connected via DVI to an Iiyama AS4315UT flat panel display with a native resolution of 1280x1024.

Apart from that problem, X works flawlessly. I've tried dpkg-reconfiguring it, didn't help, though I didn't expect it to because I can't see anything wrong with the xorg.conf (if someone wants to have a look, just ask and I'll post it).

Has anyone experienced a similar problem and perhaps even an idea how to solve it? It is annoying and the constant switching off and on is certainly not helping the backlight.

TIA,
Lars

---

### Post by lcg on 2005-11-27
I somehow solved the problem by replacing the Radeon 9000 with a Radeon 9600 I had lying around. The nice side effect was less noise as the Radeon 9600 is a newer model without active cooling.

---

