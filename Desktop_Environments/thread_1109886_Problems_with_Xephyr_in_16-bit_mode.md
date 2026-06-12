---
title: "Problems with Xephyr in 16-bit mode"
date: 2009-03-29
forum: Desktop Environments
---

### Post by lgbpinho on 2009-03-29
Hi there,

I'm trying to run a game called Wonderland online using Wine. THis game runs on 16-bit color depth. As we know, the default for Ubuntu 8.10 is 32-bit. So i'm running a nested desktop using the Xephyr as i saw on some other thread:

Xephyr :2 -ac -screen 800x600x16 &
sleep 2
DISPLAY=:2 gnome-settings-daemon &
DISPLAY=:2 nautilus -n &
DISPLAY=:2 gnome-panel &
DISPLAY=:2 metacity &

When i start the game i still have the same error, a grey window. In windows this happens whenever i try to run the game at 32-bit depth. SO the problem is really the color depth (and the support guys say the same)

any idea of how to run 16-bit applications?

---

