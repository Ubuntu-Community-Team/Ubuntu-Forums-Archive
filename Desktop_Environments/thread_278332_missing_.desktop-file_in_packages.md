---
title: "missing .desktop-file in packages"
date: 2006-10-16
forum: Desktop Environments
---

### Post by pixotec on 2006-10-16
I'm using xubuntu and installed freddroid with synaptic.
after installation I couldn't find a new menu entry to start the game (e.g. Start-Games-Freedroid) because the package didn't provide a file like

/usr/share/applications/freedroid.desktop

so I wrote it by myself:

```
# vi /usr/share/applications/freedroid.desktop
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Freedroid
Comment=A clone of Paradroid - a strategic shoot-em up
Comment[de]=Ein Paradroid-Klon
Exec=freedroid
Terminal=false
Categories=Application;Games;
```


after this a new menu entry appeared, but not under games but under Start-Andere-Freedroid (in german, in english I suppose it would be Start-Others-Freedroid)

my questions:
1. is there no rule for package-maintainers to provide a .desktop-file in their package? if not: why not?
2. where to send a .desktop-file for a package if I wrote one?
3. what is the syntax for the above example to get "Freedroid" under a new menu-category "Games" (Application;Games; didn't work...). is there an other config file to tweak?

---

### Post by CatKiller on 2006-10-16
.desktop files are, I believe, a freedesktop.org specification. You could check there for more information. 

My attempts at answering your questions:
1. I don't see why there would be a rule to include a .desktop file in all packages. If a program was to be run from the command line, for example, such a file would be completely unnecessary. They may be included in a package as a convenience if the project maintainer wanted a menu entry, but not otherwise.
2. I've put .desktop files in /usr/share/applications with some success previously. You could try a **locate .desktop** to see other places where .desktop files have been put on your computer.
3. You may have more luck with Categories=Application;Game;
That's what I've got in one of the launchers that I made myself that seems to work - I probably looked at one of the existing .desktop entries to get that.

---

### Post by CatKiller on 2006-10-16
> **pixotec said:**
> is there an other config file to tweak?

If you don't want a system-wide menu entry, you can either make a new entry with the Menu Editor or (this is largely the same thing) refer to your existing .desktop file in ~/.config/menus/applications.menu

---

