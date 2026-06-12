---
title: "Lost Fluxbox menu now shows Ubuntu's"
date: 2012-11-03
forum: Desktop Environments
---

### Post by vbmark on 2012-11-03
Hello,

I got Fluxbox to work my VPS via VNC, but when I launched something (I think it was the System Monitor) I think it started the Gnome desktop.

Now when I right click the desktop, instead of the Fluxbox menu, I get a menu for things like "Create New Folder", etc.

- Did I do something wrong?
- How do I get my Fluxbox menu back?
- How do I prevent this?

[EDIT]

I've discovered that it is running Nautilus that causes this.
To get back to Fluxbox I run xkill and then click the desktop.

Thanks!

---

### Post by bcrowell on 2013-01-27
I'm having a similar problem, but it isn't because I ran Nautilus -- I didn't.

Since updating to quantum quetzal, I'm finding that sometimes one of my fluxbox desktops loses its toolbar, and when I right-click on it, it displays a gnome menu rather than fluxbox's own root menu.

This is clearly a bug of some kind in ubuntu. If I can figure out more about what triggers the problem, maybe I can file a useful bug report.

---

### Post by LinuxMorten on 2013-10-08
First install and run gnome-tweak-tool:
[FONT=courier new]sudo apt-get install gnome-tweak-tool
[/FONT][FONT=courier new]gnome-tweak-tool[/FONT][FONT=courier new]
[/FONT]Then select "Desktop" and uncheck "Have file manager handle the desktop".

You might then have to kill all running instances of nautilus:
[FONT=courier new]sudo killall -9 nautilus[/FONT]

From now on nautilus will act as a file manager only,
and stop messing with your desktop.

I love fluxbox myself and have been using it for +10 years on various *BSD  and Linux distros.

---

