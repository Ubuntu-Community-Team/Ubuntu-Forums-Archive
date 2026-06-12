---
title: "GNOME failed to display files on desktop"
date: 2007-12-11
forum: Desktop Environments
---

### Post by shalee on 2007-12-11
I encountered a sever problem with gnome desktop. All the files on the desktop are now shown, and right click on the desktop does not give any response.

Interestingly, the panels can be loaded and applications can be launched through menus. Compiz is also running without problem. Only the desktop gives no response.

I tried to find error in /var/log/Xorg.0.log, but there was no error.

I also tried to rename ~/.gconf  to ~/.gconf.bak, but still without effect except my personal settings on panels are lost.

I looked into ~/.xsession-errors and found something like :
> (process:6502): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.


I am using Ubuntu 7.10 and Dell Latitude D820 (Nvidia card). Furthermore, i tried to install KDE4 this week, which was already removed. 
I have also checked /etc/X11/default-display-manager, which is /usr/sbin/gdm .

Could somebody kindly help me with this situation ? And where should i look into for such problems? Thanks in advance!!

---

### Post by catach on 2007-12-17
Whenever I've had my desktop icons disappear on me, restarting Nautilus has been the answer.

---

