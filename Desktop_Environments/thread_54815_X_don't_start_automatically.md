---
title: "X don't start automatically"
date: 2005-08-06
forum: Desktop Environments
---

### Post by Sargonmetal on 2005-08-06
Hi, I'm newbie on Ubuntu, sorry if you find this a little bit stupid.
I installed the nvdia drivers, and the latest linux-restricted-modules and I had to create an XF86Config-4 file copying what I had on my xorg.conf to get the X working. And it was all ok: the nvidia logo, fast 3d render, etc. But the problem is when I restart the computer I don't get any graphical itnerface. I have to log in as in the console mode and then i have to type "startx" to enter the Gnome session directly. I want to have the ubuntu login page back again, and not to start in a non-graphical mode. Could anybody help me please? I also want to know why I have to have the same file in xorg.conf and XF86Config-4, why these two same files? Thanks a lot!

Sargonmetal

---

### Post by professor_chaos on 2005-08-06
I wonder if you by accident uninstalled gdm, or it's broken.

Try reinstalling it (gdm).

---

