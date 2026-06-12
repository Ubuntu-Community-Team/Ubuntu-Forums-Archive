---
title: "Remote Desktop issues with XGL"
date: 2006-11-13
forum: Desktop Environments
---

### Post by TurkVU on 2006-11-13
I'm having some issues with remote desktop when I'm in an XGL session and haven't been able to find a fix for it. The issue is that the remote desktop session is transparent and/or only displays in 256 colors...basically its hideous looking. When I log out and back in w/ a standard GNOME desktop the remote desktop works fine.

Any solutions?

---

### Post by Aega on 2006-11-16
I've experienced the same problem, and here's the best solution I've found:

Install Xnest (System > Administration > Synaptic Package Manager > search for Xnest)

Type this in a terminal window:

Xnest -ac -terminate -geometry 1152x864+0+0 :3 & DISPLAY=:3 rdesktop -f -a 16 192.168.0.2 &

(Where 192.168.0.2 is the computer name/IP you're trying to connect to)

You can set the display size to your liking.

Hope this helps.

---

