---
title: "The desktop is to large for the screen"
date: 2007-05-07
forum: Desktop Environments
---

### Post by jørgen on 2007-05-07
When I turn on my computer the desktop is to big for my screen. If i take the mouse to one of the edges the screen moves that way. if i change to a lower resolution, and then back to the original resolution the desktop suddenly fits.  I have to do this every time i restart X or the computer.

I am using Ubuntu feisty, mobility radeon 9700 with propriatary drivers from the Restrictet drivers manager". My resolution is 1280x800.

---

### Post by NilsE on 2007-05-07
Try going into a terminal and running

sudo dpkg-reconfigure -phigh xserver-xorg

When you get to the screen for adapter type, pick the one for your adapter then when you get to the screen for resolutions just pick the one that matches your monitors native resolution.  After that do a ctrl-alt-backspace or reboot.

Basically, your xorg config is not set correctly to start and this should fix it. If this makes it worse go into the /etc/X11/ folder and copy back the latest backup to xorg.conf

---

### Post by jørgen on 2007-05-07
Thanks, it worked!

---

