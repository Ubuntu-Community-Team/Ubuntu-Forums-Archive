---
title: "xubuntu wallpaper changed independently"
date: 2016-10-29
forum: Desktop Environments
---

### Post by asgard2 on 2016-10-29
Hi,

my wallpaper changed over the day to my old wallpaper (from several month ago).

The xfce wallpaper manager still shows my new wallpaper and I can reassign wallpapers.

But how could this be even possible?

Some old xfce temporary files?
Should I clear a xfce cache folder to prevent other errors at the xfce desktop?

Using: Xubuntu 16.04

Thanks

---

### Post by Bucky Ball on 2016-10-29
With your new wallpaper set, when you reboot the machine, does the old wallpaper reappear?

On what partition is the pic you are using for your wallpaper? Is that partition being mounted when you boot the machine?

---

### Post by asgard2 on 2016-10-29
The current wallpaper is at /usr/share/... and the old one that reappeared is at a home directory.

A reboot does not change the wallaper, it happened over the day after booting and logging in, this is curious.

I don't know how to reproduce this.

---

### Post by Dennis N on 2016-10-29
The wallpaper may be set to automatically change. Check Settings > Desktop > "Change the Background" (at bottom)

---

### Post by asgard2 on 2016-10-29
@Dennis N

I know this option, but I never used it and it is deactivated. Besides these pictures are in different locations.

---

### Post by Dennis N on 2016-10-30
Best to put all the images you want to use as Desktop backgrounds in the same folder as the default backgrounds - somewhere in /usr/share/ - the exact location can vary across distros. Also, the login screen background is independent of the Desktop background, and has to be set in a different dialog.

---

