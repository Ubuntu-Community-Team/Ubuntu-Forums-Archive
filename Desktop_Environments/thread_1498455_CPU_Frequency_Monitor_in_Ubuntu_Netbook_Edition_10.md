---
title: "CPU Frequency Monitor in Ubuntu Netbook Edition 10,04"
date: 2010-05-31
forum: Desktop Environments
---

### Post by razorj7 on 2010-05-31
Hello everyone,

I am running Ubuntu Netbook Edition 10.04 on my netbook.

I noticed this version has the ability to switch between desktop environments such as Gnome Desktop and the Netbook Edition UI. When I am in Gnome, I really love using CPU Frequency Monitor available for the Gnome top panel.

My question is:
Can I use the CPU Frequency Monitor in the Netbook Edition?
If so, How?

Thank you all in advance

---

### Post by ssam on 2010-08-09
did you find a solution for this?

---

### Post by dsfitzpat on 2010-09-11
Since the panel is locked out in 10.04 it would take a bit of hacking to accomplish it.  I'm not sure how to pull it off.  One thing to try would be to use the gnome desktop session and configure it to look like the netbook session - since in the desktop session you can do whatever you want to the panel.  You might try something like this:
1. Login to the desktop session
2. Delete the bottom panel.
3. Remove the Ubuntu menu from the top.
4. Add in the window picker applet and the cpu monitor.
5. In the start up preferences, add maximus and netbook-launcher

The warning here is that you'd then be running netbook launcher over top of regular gnome, instead of running it as an independent desktop - so it's not an ideal solution.  The other warning is that I tried this after installing 10.10 beta, which has switched to a new netbook interface - and I was trying this out as a way to get the old one back.

Alternatively, you could try running Docky (or AWN) at the bottom of the screen.  The HUD theme in Docky goes well with the default theme for UNE 10.10, and you can add a CPU monitor applet (it's colour-based: green for low CPU, red for high).  You can set Docky to 'intellihide' mode, so that it drops out of sight whenever an application needs the whole screen.

---

