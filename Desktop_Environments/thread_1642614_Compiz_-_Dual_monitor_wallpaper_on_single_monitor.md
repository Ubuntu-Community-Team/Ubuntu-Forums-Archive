---
title: "Compiz? - Dual monitor wallpaper on single monitor"
date: 2010-12-10
forum: Desktop Environments
---

### Post by Syrinx Priest on 2010-12-10
Is there any way to put a dual monitor wallpaper on a single monitor configuration using desktop wall? Using only 1/3 or so per wall. Something that will have the effect like the scrolling wallpaper feature on Android/iPhone. Thanks in advance.

---

### Post by Sam Lars on 2010-12-11
You'll need to install compiz-config-settings-manager and compiz-fusion-plugins-extra (and be using the Compiz desktop effects). This will give Compiz control of your desktop instead of Nautilus, so you will not be able to have your icons on the desktop, and Compiz will manage your desktop images.

System> Preferences > Advanced Desktop Settings
Find the Wallpaper plugin and enable it. Add the images you want to use.
And to get Nautilus to give up control of the desktop, run gconf-editor
apps > nautilus > preference, deselect "Show Desktop"

If you want to revert your changes, you can back and select "Show Desktop" again and Nautilus will be back in business.

Instructions from here:
[http://www.ghacks.net/2010/01/15/multiple-wallpapers-in-compiz/](http://www.ghacks.net/2010/01/15/multiple-wallpapers-in-compiz/)

---

### Post by Syrinx Priest on 2010-12-13
Yeah, Thanks. I guess it was on a sticky....whoops. I blame being tired zZzZz-_-zZzZz

---

