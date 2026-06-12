---
title: "Installing Ubuntu Studio w/o DVD Drive"
date: 2007-08-05
forum: Dell  Ubuntu Support
---

### Post by iAndrew on 2007-08-05
Hi, I recently found my old Inspiron 1150. It's not that great on Windows, and is slower then the current computers.

But I was thinking to convert it to Linux, just for testing.

But the main problem I found, pre-installation was:

What do I do!? I have no DVD Drive.

I've searched for this, I might not being using keywords.

Also I don't know if I posted this in the right forum or not, because I was also thinking this should go to Installations & Upgrades forum.

---

### Post by fluteflute on 2007-08-05
Have you got a CD drive? If so install Ubuntu from CD and then install Studio on top.

---

### Post by logos34 on 2007-08-05
> Have you got a CD drive? If so install Ubuntu from CD and then install Studio on top.

If you have a cd drive that's probably your best bet.  Then install the desktop metapackage:

**sudo apt-get install ubuntustudio-desktop**

and add any others you desire that are not included in the above,

> ubuntustudiolauncher - Music applications launcher
ubuntustudio-audio - Ubuntu Studio Audio Package
ubuntustudio-video - Ubuntu Studio video Package
ubuntustudio-audio-plugins - Ubuntu Studio audio plugins Package
ubuntustudio-desktop - Ubuntu Studio Desktop Package
ubuntustudio-graphics - Ubuntu Studio graphics Package
ubuntustudio-gdm-theme - Ubuntu Studio - GDM theme
ubuntustudio-icon-theme - UbuntuStudio Icon theme
ubuntustudio-look - Ubuntustudio look - metapackage
ubuntustudio-session-splashes - Ubuntu Studio look - Session splashes
ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers
usplash-theme-ubuntustudio - Usplash theme for Ubuntustudio
ubuntustudio-default-settings - Default settings and artwork for the UbuntuStudio desktop
ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
ubuntustudio-artwork - UbuntuStudio themes and artwork
ubuntustudio-screensaver - UbuntuStudio screensaver


---

