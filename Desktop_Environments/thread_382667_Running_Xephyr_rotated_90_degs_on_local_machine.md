---
title: "Running Xephyr rotated 90 degs on local machine"
date: 2007-03-12
forum: Desktop Environments
---

### Post by MagnusL on 2007-03-12
Hi!

I'd need to run a nested xserver, rotated 90 degrees on my tablet laptop (since Xrandr does not work with the xserver on it). It seems Xephyr could help me do that, and I have installed xserver-xephyr and can run it. But: how do I start a window manager in it (xfce4) and how to rotate it 90 dregrees?

The way I do this today is from a virtual terminal run:
$ startx -- :1 -layout Rotate

Rotate is defined in xorg.conf. So how can I do the same from within the running x session? (edgy, KDE or XFCE4). 

Magnus L

---

