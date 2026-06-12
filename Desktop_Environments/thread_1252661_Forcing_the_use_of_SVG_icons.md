---
title: "Forcing the use of SVG icons"
date: 2009-08-29
forum: Desktop Environments
---

### Post by petit.padavoine on 2009-08-29
I sought to replace the logo on the applications menu.
I had an alternate SVG icon, I located the original one (usr/share/icons/Human/scalable/places/start-here.svg, backed it up, and replaced it with my own).

```

gtk-update-icon-cache
killall-panel

```

Nothing, still the old icon. It turned out that instead of using the high-quality SVG icon, the system was using a small resolution PNG icon.
I had to go on a crusade to delete every single other start-here icon part of the Human icon theme.

```

locate start-here
rm /22*22/places/start-here.png
rm /24*24/places/start-here.png
rm /48*48/places/start-here.png

```

It did work, but it lead me to wonder: surely there would have been a simpler way involving telling the system to use the SVG icon and not the PNG icons. C/D?

Also, on a sidenote, any links to SVG Mac OS X icons (even individual icons, not necessarily a whole pack), are appreciated. SVG only though.

---

### Post by petit.padavoine on 2009-08-31
Bump?

---

### Post by Andrew_P on 2012-11-27
> **petit.padavoine said:**
> I sought to replace the logo on the applications menu.
I had an alternate SVG icon, I located the original one (usr/share/icons/Human/scalable/places/start-here.svg, backed it up, and replaced it with my own).
```
gtk-update-icon-cache
killall-panel
```

Nothing, still the old icon. It turned out that instead of using the high-quality SVG icon, the system was using a small resolution PNG icon.
I had to go on a crusade to delete every single other start-here icon part of the Human icon theme.

According to GNOME documentation, *"gtk-update-icon-cache expects to be given the path to a icon theme directory containing an index.theme, e.g. /usr/share/icons/hicolor, and writes a icon-theme.cache containing cached information about the icons in the directory tree below the given directory."*  The best way to use the [FONT="Lucida Console"]*gtk-update-icon-cache*[/FONT] command is in a script that steps through *all* the various theme directories and updates the cache for all of them.  Get the attached BASH script, make it executable and run it as root, *i.e.*,
```
sudo ./rebuild-icon-cache.sh
```

"[FONT="Lucida Console"]*killall-panel*[/FONT]" isn't a valid command.  To force restart of the GNOME panel, use:
```
killall gnome-panel
```

Finally, put a PNG or XPM copy of the icon you wish to use in /usr/share/pixmaps, 32x32 or 48x48 pixels in size, preferably before you try to change an icon in a launcher or create a custom launcher.  It appears that if GNOME can't find an icon in one of the themes, it defaults to looking for it in the pixmaps directory when you right-click on an item in the Applications menu and select "Add this launcher to desktop".  If you still don't get SVG icons in the copy of the launcher that you placed on the desktop, you may have to resort to opening the application's desktop entry in ~/.local/share/applications with a text editor such as gedit and manually modify the line that starts with "Icon=" to explicitly give the full path to the SVG icon file.  It's crufty and buggy, but, hey, it's Linux.

---

