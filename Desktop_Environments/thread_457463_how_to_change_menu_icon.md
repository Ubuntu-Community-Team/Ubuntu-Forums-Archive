---
title: "how to change menu icon?"
date: 2007-05-28
forum: Desktop Environments
---

### Post by volksolwagen57 on 2007-05-28
i want to change the ubuntu logo on the panel next to the applications tab. the colors don't match with my theme and i'd like to find a dark blue ubuntu logo. does anybody know?

---

### Post by Blender on 2007-05-28
I think the icon is called **distributor-logo**, but I am not sure.
```

[~] $ cd /usr/share/icons 
[share/icons] $ find . -name 'distributor-logo*'
./Tangerine/scalable/places/distributor-logo.svg
./Tangerine/16x16/places/distributor-logo.png
./Tangerine/24x24/places/distributor-logo.png
./Tangerine/22x22/places/distributor-logo.png
./Tangerine/32x32/places/distributor-logo.png
./hicolor/48x48/apps/distributor-logo.png
./gnome/16x16/places/distributor-logo.png
./gnome/scalable/places/distributor-logo.svg
./gnome/22x22/places/distributor-logo.png
./gnome/24x24/places/distributor-logo.png
./gnome/32x32/places/distributor-logo.png
./Human/scalable/places/distributor-logo.svg
./Human/22x22/places/distributor-logo.png
./Human/24x24/places/distributor-logo.png
./Human/48x48/places/distributor-logo.png
./Tango/scalable/places/distributor-logo.svg

```
Please note that some of these files are symlinks:
```

[share/icons] $ find . -name 'distributor-logo*' -exec file '{}' \;
./Tangerine/scalable/places/distributor-logo.svg: symbolic link to `start-here.svg'
./Tangerine/16x16/places/distributor-logo.png: symbolic link to `start-here.png'
./Tangerine/24x24/places/distributor-logo.png: symbolic link to `start-here.png'
./Tangerine/22x22/places/distributor-logo.png: symbolic link to `start-here.png'
./Tangerine/32x32/places/distributor-logo.png: symbolic link to `start-here.png'
./hicolor/48x48/apps/distributor-logo.png: PNG image data, 48 x 48, 8-bit/color RGBA, non-interlaced
./gnome/16x16/places/distributor-logo.png: symbolic link to `start-here.png'
./gnome/scalable/places/distributor-logo.svg: symbolic link to `start-here.svg'
./gnome/22x22/places/distributor-logo.png: symbolic link to `start-here.png'
./gnome/24x24/places/distributor-logo.png: symbolic link to `start-here.png'
./gnome/32x32/places/distributor-logo.png: symbolic link to `start-here.png'
./Human/scalable/places/distributor-logo.svg: symbolic link to `start-here.svg'
./Human/22x22/places/distributor-logo.png: symbolic link to `start-here.png'
./Human/24x24/places/distributor-logo.png: symbolic link to `start-here.png'
./Human/48x48/places/distributor-logo.png: symbolic link to `start-here.png'
./Tango/scalable/places/distributor-logo.svg: symbolic link to `start-here.svg'

```
**start-here.*** are all regular files (either PNG or SVG).

Don't forget to make a backup copy of the files you replace (or reinstall the theme packages).

Hope this helps.

---

### Post by fakeollie on 2007-06-17
Here's an idea: instead of altering the default themes, you can go to your ~/.icons (ie, /home/username/.icons) and add the icons you want to replace there. 

I'll give you an example. If your current icon theme is Human (check on System > Preferences > Themes), just create a ~/.icons/Human dir and add the icons you want to replace there.

Go to /usr/share/icons/Human and study the structure. Re-create a similar folder layout on your ~/.icons/Human for your own icons. If you're using a different theme, adjust the path accordingly.

For the ubuntu icon on Applications, for example, you should create ~/.icons/Human/22x22/places and put your replacement distributor-logo.xxx (png, svg, etc.) there. Once you have the icons there, open a terminal and kill gnome-panel.

```
killall gnome-panel
```The icons on your .icons take precedence over the ones in /usr/share/icons and you can also use it to replace specific icons, like filetypes (mp3, txt, doc) or other icons (look at the mimetype directories). This method is also a good idea because you won't lose your changes in a system upgrade/re-install (providing you keep your /home folder intact).

Hope this helps. Cheers.

---

### Post by lunamystry on 2007-09-13
em... What about the k-menu. can I change that?

---

### Post by Spr0k3t on 2007-09-13
Thanks for the tip fakeollie... I didn't know about editing the ~/.icons .  That would make it much easier to keep the theme the same across multiple computer systems.

---

