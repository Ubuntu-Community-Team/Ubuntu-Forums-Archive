---
title: "[SOLVED] Openbox problem after upgrading to 3.4.5"
date: 2008-01-12
forum: Desktop Environments
---

### Post by Gigamo on 2008-01-12
Hi. I just tried to upgrade my openbox to the latest 3.4.5, by compiling from source since there aren't any .deb packages yet. All went fine, but now I no longer have an Openbox option in the Sessions in GDM login screen.

Help appreciated. :)

---

### Post by urukrama on 2008-01-12
Strange. I still have all the session menus. Did you remove the old version first?

In the source archive, you'll find the session files (In data > xsession). You need the Openbox file that looks like this:
> [Desktop Entry]
Encoding=UTF-8
Name=Openbox
Comment=Log in using the Openbox window manager (without a session manager)
Exec=@bindir@/openbox-session
TryExec=@bindir@/openbox-session
Icon=openbox.png
Type=XSession


If you like the Gnome/Openbox or KDE/Openbox ones as well, use those too. Copy the files to /usr/share/xsessions and edit the @bindir@ in each file to match the location on your system (should be /usr/local/bin or /usr/bin, depending on how you configured the package).

You might have to make theme executable (using chmod +x /location/of/file). Reboot, and they should show up in the sessions menu.

---

### Post by Gigamo on 2008-01-13
> **urukrama said:**
> Strange. I still have all the session menus. Did you remove the old version first?

In the source archive, you'll find the session files (In data > xsession). You need the Openbox file that looks like this:


If you like the Gnome/Openbox or KDE/Openbox ones as well, use those too. Copy the files to /usr/share/xsessions and edit the @bindir@ in each file to match the location on your system (should be /usr/local/bin or /usr/bin, depending on how you configured the package).

You might have to make theme executable (using chmod +x /location/of/file). Reboot, and they should show up in the sessions menu.

Thanks mate - worked like a charm :)

---

