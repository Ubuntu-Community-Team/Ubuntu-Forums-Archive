---
title: "Best way to theme ubuntu"
date: 2009-03-25
forum: General Help
---

### Post by ftaylor on 2009-03-25
Hey folks,

what's the best way to change the ubuntu theme? I've been looking at all these sister sites, the gnome-look.org et al. They all lack an explanation as to what to do with the theme files.

I currently have emerald installed, but all the themes I've been downloading are metacity themes. What do I do with the files?

Cheers,

Finbarr

---

### Post by 3rdalbum on 2009-03-25
Ubuntu is more intuitive than a lot of people think.

To install a theme, just drag the .tar.gz file onto the window where you can change themes (System > Preferences > Appearance) or click the "Install..." button within that window.

---

### Post by mcduck on 2009-03-25
All GTK2, icon and Metacity themes can be installed by drag&dropping the theme package to the Appearance-window, just like 3rdalbum said.

If it's a complete theme (ie. it includes all GTK2 theme, icons and Metacity theme) it will appear directly in the appearance-window. otherwise you need to click "Customize" and select the individual theme components you wish to use.

Emerald themes are installed through the Emerald Theme Manager (which you need to install if you wish to use Emerald).

GDM themes are installed in System/Administration/Login Screen.

For Usplash and Grub themes I recommend installing Startup Manager.


And to explain the different themes a bit:

GTK2 themes define how your programs look like,buttons, widget spacing, colors and so on. (there are also GTK1 themes around, but ignore them as you are not likely to have any pr0ograms that would still use GTK1)

Metacity and Emerald themes are for window borders. Both Metacity and Compiz are able to use Metacity themes, to use Emerald themes instead you need to use Compiz and configure it to use Emerald as it's window decorator.

GDM themes change how your login screen looks like.

---

### Post by ftaylor on 2009-03-25
Thanks for your help folks. Didn't realise it was as easy as this. Emerald => uninstalled.

---

