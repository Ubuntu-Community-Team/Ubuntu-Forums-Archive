---
title: "qtcurve"
date: 2010-10-29
forum: Desktop Environments
---

### Post by Clove7 on 2010-10-29
Hi, I've downloaded qtcurve, and I've got a theme for it...but I can't find it anywhere, and I don't know how to load anything into qtcurve. Can someone help me please?

---

### Post by ankspo71 on 2010-10-30
Hi,
If you have the KDE desktop installed, you can enable and configure qtcurve by going to System Settings > Application Appearance > Style > then where it says "Widget Style", select qtcurve from the dropdown list, then click apply. You can import your qtcurve theme and configure it by clicking on the "Configure" button next it.

I don't know how you can do this in Ubuntu's own (Gnome) desktop though.
Hope this helps.

---

### Post by FlameReaper on 2010-10-30
If you're using GNOME:

First of all put the folder (along with its contents of course) of the qtcurve theme (if it's zipped, uncompress it) you downloaded into the folder ".themes" which is located in your home directory. It's a hidden folder, so you might need to enable viewing hidden files and folders in Nautilus (which can be done by pressing Ctrl+H).

... Or to be honest, you actually don't need to download it at all and go through the whole process... QtCurve is available from the repository with the package name "gtk2-engines-qtcurve" and you can install it by:

```
sudo apt-get install gtk2-engines-qtcurve
```

Then go to the desktop, right click it and select "Change Desktop Background" or go to System > Preferences > Appearance.

then go to the "Theme" tab and click the Customize button. It should appear in the list from the "Controls" tab.

---

