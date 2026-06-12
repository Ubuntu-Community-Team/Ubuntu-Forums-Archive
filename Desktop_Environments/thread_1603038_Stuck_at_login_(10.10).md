---
title: "Stuck at login (10.10)"
date: 2010-10-22
forum: Desktop Environments
---

### Post by HappyJaZZ on 2010-10-22
Hey! Basically this is a follow-up to [this thread.]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1600559")

Basically, I'm stuck at the GDM login window. When I try to login the screen turns black for a second, and returns me at the GMD login.

I have removed all nvidia drivers
I have reinstalled GDM
I have reinstalled the X server

Still no succes.

I had some succes at a time when I replaced GDM with WDM, but I don't think WDM loads the bashrc file, so fixing GDM would be the way to go.

Thanks in advance!

EDIT:

Just found out that the command "startx" works fine when I'm in the recovery console, so maybe the program is simply to make GDM run the "startx" command?

EDIT2:

When I am logged in as root (I run startx from the recovery root terminal), and presses "Switch from root", I get the following warning:

**Unable to start new display**
The name org.gnome.DisplayManager was not provided by any .service files

---

### Post by sikander3786 on 2010-10-22
Is it a clean install of Maverick? Or and upgrade from the previous version?

If upgrade, did you remove the proprietary drivers before upgrading?

---

### Post by HappyJaZZ on 2010-10-22
It is a clean install.

Anyways, I found the problem!

I edited my /etc/environment file, since I thought it would be able to source the environment for my intel fortran compiler. However, it seemed like that didn't work, and instead made the xserver crash (or something like that).

Restoring /etc/environment to its previous state solved everything!

---

