---
title: "Tip: Installing New Lock Dialog Theme on Lucid/Karmic"
date: 2010-05-22
forum: Desktop Environments
---

### Post by daybird on 2010-05-22
For the last couple of ubuntu versions, gnome-screensaver, which is also the gnome screen-locking program, has been using gtkbuilder .ui files for configuration; unfortunately almost all of the third-party themes (e.g. on gnome-look.org) use .glade files.  Here's how to convert a .glade file to a .ui file for use with current versions of gnome-screensaver:
1.  Open a shell
2.  Unpack your downloaded theme file
3.  run this command: gtk-builder-convert -w mynewtheme.glade mynewtheme.ui.  The -w switch is important.  The gtk-builder-command should already be installed on your system, but if not, it is a script which you can google and run directly from your download directory.
4.  transfer the theme files, including the unmodified .gtkrc, to /usr/share/gnome-screensaver.  Do not stash the config files in a subdirectory.
5. change the gconf setting (e.g. with gconf-editor) of /apps/gnome-screensaver/lock-dialog-theme to your new theme (e.g. "burst", or "arc-colors-human").

---

### Post by Mnemic on 2010-05-25
> **daybird said:**
> For the last couple of ubuntu versions, gnome-screensaver, which is also the gnome screen-locking program, has been using gtkbuilder .ui files for configuration; unfortunately almost all of the third-party themes (e.g. on gnome-look.org) use .glade files.  Here's how to convert a .glade file to a .ui file for use with current versions of gnome-screensaver:
1.  Open a shell
2.  Unpack your downloaded theme file
3.  run this command: gtk-builder-convert -w mynewtheme.glade mynewtheme.ui.  The -w switch is important.  The gtk-builder-command should already be installed on your system, but if not, it is a script which you can google and run directly from your download directory.
4.  transfer the theme files, including the unmodified .gtkrc, to /usr/share/gnome-screensaver.  Do not stash the config files in a subdirectory.
5. change the gconf setting (e.g. with gconf-editor) of /apps/gnome-screensaver/lock-dialog-theme to your new theme (e.g. "burst", or "arc-colors-human").
Thanks a lot mate, that solved my problem!!

---

### Post by un234567 on 2010-05-26
Awesome! solved another problem :guitar:

---

### Post by meskes on 2010-08-25
Anyone happen to know the source package for this since it seems that it's not installed on my system?

---

### Post by igorp1024 on 2010-09-06
You need to install libgtk2.0-dev

---

