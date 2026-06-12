---
title: "Problems with start up applications"
date: 2010-08-10
forum: Desktop Environments
---

### Post by Spice Weasel on 2010-08-10
I am trying to make my xfce4 install as minimal as possible on start up by removing as many applications as I can, the problem is that some of them just don't want to not start up and others seem to want to open as many of themselves as possible. Here are the programs that I am having trouble  with:

Parcellite - Set to run on start up, opens itself twice.
gnome-keyring-daemon - Opens itself twice for no reason.
gnome-screensaver - I have no idea why this is running, and it's getting annoying having to kill it each time I log in.
gnome-panel - Again, I have no idea why this happens, and it only just started today. Has to be killed several times before eventually closing.

Thanks.

---

### Post by Spice Weasel on 2010-08-10
The problem was GNOME's session manager interfering with XFCE's. I just solved it the cheap way and removed most things gnome-related.

---

