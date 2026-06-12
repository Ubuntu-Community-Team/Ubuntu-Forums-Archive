---
title: "Gnome (gdm) won't run on a remote Cygwin desktop"
date: 2009-09-17
forum: Desktop Environments
---

### Post by BillRebey on 2009-09-17
I have a Ubuntu 9.04 box, and I want to run the Gnome Desktop Manager (gdm) and have it show up on my Windows desktop via Cygwin.

I'm using Cygwin's SSH with "ssh -Y" to log into the Ubuntu box from windows and get X-traffic forwarding.  Other X apps that I start from the SSH login work fine and show up on my Windows desktop as expected - xfontsel, xcalc, and so on.  

When I run gdm, though, the display isn't routed to the Windows box, but rather shows up locally at the Ubuntu box.

What am I missing?

---

