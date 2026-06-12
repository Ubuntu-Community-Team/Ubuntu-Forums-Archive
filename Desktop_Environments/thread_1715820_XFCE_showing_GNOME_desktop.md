---
title: "XFCE showing GNOME desktop"
date: 2011-03-27
forum: Desktop Environments
---

### Post by okok on 2011-03-27
I am the latest stable Ubuntu (10.10) on an Asus netbook and have both GNOME an XFCE installed. I started with Gnome and than installed XFCE because it works slightly faster on that slow computer.

In the beginning everything was fine, but at some point, I don't know when (but it was so also when I was running ubuntu 9.10, before I upgraded to 10), this is what started to happen: when I log in and choose XFCE, I first see my XFCE desktop, then it flickers back and forth between my XFCE and Gnome desktop (but the top panel remains the XFCE one), and eventually it settles on the GNOME desktop (which has its own color, different icons in different positions, and its own context menus).

The general desktop environment is XFCE: the desktop panel and the itmes on it are XFCE, but the desktop area itself is my GNOME desktop.

Any idea why this happens and what I can do to get rid of the display of the GNOME desktop when I choose to use XFCE?

---

### Post by SantaFe on 2011-03-27
Same thing happened to me.  [https://forum.xfce.org/viewtopic.php?id=5484](https://forum.xfce.org/viewtopic.php?id=5484)

It may be your running Nautilus in the background.  You might try killing it in System Monitor, and making sure it's not listed in Session and startup/session and reboot with automatically save session on logout.

---

### Post by okok on 2011-03-28
Thank you. You were right. Nautilus was running at startup, and disabling it solved the problem. I am wondering, though, why it was starting in the first place. I can't see any effect its disablement has on the running of anything else, including GNOME applications.

---

### Post by SantaFe on 2011-03-28
Not sure why it decided to start doing that, unless something you used in Xfce needed it & it decided to stick around.  In my case, I was playing around with XfApplet & tried using the GNOME trash Can panel applet in Xfce.  Had to go back to the Xfce one.

---

### Post by okok on 2011-03-29
The only thing I can think of (perhaps because I am not a very technically knowledgeable linux user) that I use that may require nautilus  is Dropbox, that is described as "nautilus plugin". But it works as well after I removed nautilus from the list of auto-starting programs.

---

### Post by nzjethro on 2011-06-13
> **SantaFe said:**
> Same thing happened to me.  [https://forum.xfce.org/viewtopic.php?id=5484](https://forum.xfce.org/viewtopic.php?id=5484)

It may be your running Nautilus in the background.  You might try killing it in System Monitor, and making sure it's not listed in Session and startup/session and reboot with automatically save session on logout.

Cool, worked for me too.

---

