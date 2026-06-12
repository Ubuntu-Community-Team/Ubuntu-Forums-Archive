---
title: "Top Bar Pixel Width Stuck"
date: 2008-08-04
forum: Desktop Environments
---

### Post by jonnyrockets on 2008-08-04
i just recently upgraded from 7.10 to 8.04. it was a bit rocky at times, especially when locales was installing it froze up a few times and i had to tackle it from command line. 

anyhow, my top bar has a pixel width of 23, or its set to a pixel width of 23. however, the icon in top left (ubuntu icon) seems to be stuck at 32 pixels high. 

so even though the bar itself is set to 23, that icon is stuck at 32, and it makes the rest of the bar "fat". 

does anyone know the location of the icon in the top left? i am thinking i will just resize it down to 24x24 and all will be well. 

thanks in advance!

---

### Post by pauper on 2008-08-05
Find out what theme and set of icons are currently in use:

```
grep -C 5 "icon_theme" $HOME/.gconf/desktop/gnome/interface/%gconf.xml
```

Make note of icon_theme and gtk_theme values.

Human theme default menu icons:

```
:~$ **find /usr/share/icons -iname *start-here* 2> /dev/null**
/usr/share/icons/Tangerine/16x16/places/start-here.png
/usr/share/icons/Tangerine/22x22/places/start-here.png
/usr/share/icons/Tangerine/32x32/places/start-here.png
/usr/share/icons/Tangerine/24x24/places/start-here.png
/usr/share/icons/Tangerine/scalable/places/start-here.svg
/usr/share/icons/gnome/16x16/places/start-here.png
/usr/share/icons/gnome/22x22/places/start-here.png
/usr/share/icons/gnome/32x32/places/start-here.png
/usr/share/icons/gnome/24x24/places/start-here.png
/usr/share/icons/gnome/scalable/places/start-here.svg
/usr/share/icons/Human/48x48/places/start-here.png
/usr/share/icons/Human/22x22/places/start-here.png
/usr/share/icons/Human/24x24/places/start-here.png
/usr/share/icons/Human/scalable/places/start-here.svg

```

> The icon lookup mechanism has two global settings, the list of base
directories and the internal name of the current theme. Given these we need to
specify how to look up an icon file from the icon name and the nominal size.

The lookup is done first in the current theme, and then recursively in each of
the current theme's parents, and finally in the default theme called "hicolor"
(implementations may add more default themes before "hicolor", but "hicolor"
must be last). As soon as there is an icon of any size that matches in a
theme, the search is stopped. Even if there may be an icon with a size closer
to the correct one in an inherited theme, we don't want to use it. Doing so
may generate an inconsistent change in an icon when you change icon sizes
(e.g. zoom in).

The lookup inside a theme is done in three phases. First all the directories
are scanned for an exact match, e.g. one where the allowed size of the icon
files match what was looked up. Then all the directories are scanned for any
icon that matches the name. If that fails we finally fall back on unthemed
icons. If we fail to find any icon at all it is up to the application to pick
a good fallback, as the correct choice depends on the context.

Source:

[http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html](http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html).

Check this string "gtk-icon-sizes = "panel-menu=??,??""

```
gedit /usr/share/themes/Human/gtk-2.0/gtkrc
```

Find out about lookup pattern for the current theme:

```
gedit /usr/share/icons/Human/index.theme
```

Read up about mime:

```
evince /usr/share/doc/shared-mime-info/shared-mime-info-spec.pdf
```

```
man update-panels
man update-mime
man update-mime-database
```

---

