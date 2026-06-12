---
title: "[Hoary] Adding Xfce to GDM does not work?"
date: 2005-03-22
forum: Desktop Environments
---

### Post by Nicolinux on 2005-03-22
Hi,

I compiled Xfce 4.2.1.1 and would like to add it to the GDM selection. I tried:

/etc/X11/sessions/
/etc/dm/Sessions/
/usr/share/gdm/BuiltInSessions/
/usr/share/xsessions/

and placed there a xfce42.desktop file.

This is the xfce42.desktop file:
[Desktop Entry]
Encoding=UTF-8
Name=Xfce 4.2 Session
Comment=Use this session to run Xfce 4.2 as your desktop environment
Exec=/usr/local/bin/startxfce4
Icon=/usr/local/share/pixmaps/xfce4_xicon1.png
Type=Application


After that I restarted GDM to no avail and the Xfce entry does not appear.
Any idea why?

Thanks much,
Stefan

---

### Post by Glanz on 2005-03-22
cp /path/to/your/xfce42.desktop /usr/share/xsessions/xfce42.desktop

as superuser, of course...

---

### Post by Nicolinux on 2005-03-22
Ahhh... thanks,
but I allready tried /usr/share/xsessions/xfce42.desktop.


Stefan.

---

### Post by Glanz on 2005-03-22
Make sure it points to /usr/local/bin/startxfce4 . If you had an old " .desktop" file for the Ubuntu package of XFCE pointing to /usr/bin/startxfce the newer xfce42 wont launch.
If that doesn't work...
Perhaps
dpkg-reconfigure gdm
or
a reinstallation of GDM

---

