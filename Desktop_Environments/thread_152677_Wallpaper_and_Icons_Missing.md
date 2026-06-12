---
title: "Wallpaper and Icons Missing"
date: 2006-03-30
forum: Desktop Environments
---

### Post by StkvDba on 2006-03-30
When the desktop comes up, **I am missing my wallpaper and the icons **for files in Desktop/.  In addition, a right mouse-click on the desktop does not bring up the context menu.  The Panel(s) seem to be ok, and within an application the mouse works fine as well.

**What happened before**:  I compiled a 2.6.12 kernel to get a Wacom Graphire4 tablet working.  The compilation and installation went smoothly.  Then, **I modified my xorg.conf **for the tablet, using HOWTOs from these forums.  In one of these, the author said to restart the Xserver without rebooting, using CTRL-ALT-BKSP.  I did this and got a login prompt. Logging in, I did 'startx' to get back in.  The display came up, with wallpaper, etc., but **I got repeated error messages **popping up that another running panel was detected.  I rebooted, and here I am today without wallpaper, icons, or right mouse-click.

I'm a relatively new Linux convert (from Windows), but not without technical skills.  Any detailed help you could provide in pointing me in the right direction would be appreciated.  I'm sure it's probably another config file somewhere I don't know about yet.  Meanwhile, I'll try my old xorg.conf...

---

### Post by ardchoille on 2006-03-30
[QUOTE=StkvDba]When the desktop comes up, **I am missing my wallpaper and the icons **for files in Desktop/.  In addition, a right mouse-click on the desktop does not bring up the context menu.  The Panel(s) seem to be ok, and within an application the mouse works fine as well.

**What happened before**:  I compiled a 2.6.12 kernel to get a Wacom Graphire4 tablet working.  The compilation and installation went smoothly.  Then, **I modified my xorg.conf **for the tablet, using HOWTOs from these forums.  In one of these, the author said to restart the Xserver without rebooting, using CTRL-ALT-BKSP.  I did this and got a login prompt. Logging in, I did 'startx' to get back in.  The display came up, with wallpaper, etc., but **I got repeated error messages **popping up that another running panel was detected.  I rebooted, and here I am today without wallpaper, icons, or right mouse-click.

I'm a relatively new Linux convert (from Windows), but not without technical skills.  Any detailed help you could provide in pointing me in the right direction would be appreciated.  I'm sure it's probably another config file somewhere I don't know about yet.  Meanwhile, I'll try my old xorg.conf...[/QUOTE]

OK, nautilus, the file manager in gnome, is responsible for drawing the desktop wallpaper and icons. If, for some reason, nautilus is not starting when gnome loads, then you won't have desktop wallpaper or icons. So, it sounds like you need to find out why nautilus is not starting up when gnome loads.

Until you find a solution to your problem, you can run nautilus and it will fix your wallpaper and icons. Just run this from ALT+F2 or from a terminal:
```

nautilus --no-default-window --sm-client-id default2 &

```
The "&" puts the entire process in the background so you can close your terminal without having the process killed.

---

### Post by StkvDba on 2006-03-30
Thank you ardchoille!

Taking your hint, I went to Applications -> System Tools -> **Configuration Editor**, and drilled down through desktop -> gnome -> applications -> browser.  There, I found the **default browser had been changed **to "epiphany."  I changed it back to "nautilus" and am again a **happy Ubuntuan**!

---

