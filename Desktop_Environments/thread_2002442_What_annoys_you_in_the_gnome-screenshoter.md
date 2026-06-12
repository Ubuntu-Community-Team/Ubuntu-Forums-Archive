---
title: "What annoys you in the gnome-screenshoter?"
date: 2012-06-12
forum: Desktop Environments
---

### Post by t1497f35 on 2012-06-12
Hi,
If you have any gripes with the default screenshot tool on Ubuntu please share.

My top 2 ones are:
1) It flashes the screen which hurts my eyes especially when I sit in a dark room
2) Doesn't remember the last location I saved to.

So I created my own tool (attached) with a few additional options (like saving as JPEG).

PS:
The binary included is for amd64.
If you're using i386:
1) install cmake and libgtkmm-3.0-dev
2) open the terminal in the $source/bin folder
3) cmake ..
4) make


To replace the default screenshot tool:
1) backup the file /usr/bin/gnome-screenshot
2) copy your new app to that folder and rename to "gnome-screenshot".

---

