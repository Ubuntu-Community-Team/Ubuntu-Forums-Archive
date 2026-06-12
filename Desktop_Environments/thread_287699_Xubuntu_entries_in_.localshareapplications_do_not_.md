---
title: "Xubuntu: entries in .local/share/applications do not appear in menu"
date: 2006-10-29
forum: Desktop Environments
---

### Post by _savior_ on 2006-10-29
Hello,

I have installed Xubuntu Edgy yesterday, and I have a problem with it. My /home was in a different partition, so the settings were not overwritten during the install. Everything is fine; however, the menu items in ~/.local/share/applications are not shown in the system menu.

Before the reinstall, I was running Gnome, and the entries were created with Alacarte. But I don't think this really matters. The directory contains the following files: 
```
-rw-r--r-- 1 savior savior  266 2006-10-29 09:38 clisp.desktop
-rw------- 1 savior savior   23 2006-10-28 17:20 defaults.list
-rw-r--r-- 1 savior savior 9760 2006-10-15 16:44 gconf-editor.desktop
-rw-r--r-- 1 savior savior 7359 2006-10-15 16:44 gnomecc.desktop
-rw------- 1 root   root    416 2006-10-13 19:27 googleearth.desktop
-rw-r--r-- 1 savior savior  282 2006-10-15 16:44 hp-toolbox.desktop
-rw-r--r-- 1 savior savior  296 2006-10-07 21:32 jEdit.desktop
-rw-r--r-- 1 savior savior  189 2006-10-22 15:03 skype.desktop
-rw-r--r-- 1 savior savior  347 2006-10-06 20:10 uqm.desktop
```

For example, uqm looks like:
```
[Desktop Entry]
Categories=Application;Game;StrategyGame;
Comment=Open source version of Star Control II
Comment[en_US]=Open source version of Star Control II
Encoding=UTF-8
Exec=uqm
Icon=/usr/share/icons/uqm_big.png
Icon[en_US]=/usr/share/icons/uqm_big.png
Name=The Ur-Quan Masters
Name[en_US]=The Ur-Quan Masters
Terminal=false
Type=Application
```

Does anyone have any idea how to make the system aware of them?

Thanks,
Savior

---

### Post by NeoLithium on 2006-10-29
Even though you were running GNOME before; xfce, which is the window manager for xubuntu; not all the programs are interchangable.  There's quite a few different programs for GNOME that can't work for KDE, and others that need one of those 2 desktop environments that will nto work for the other window managers (such as xfce, flux or icewm).

---

### Post by _savior_ on 2006-10-29
> **NeoLithium said:**
> Even though you were running GNOME before; xfce, which is the window manager for xubuntu; not all the programs are interchangable.  There's quite a few different programs for GNOME that can't work for KDE, and others that need one of those 2 desktop environments that will nto work for the other window managers (such as xfce, flux or icewm).

Yes, but if you have a look at the list of applications in question, you can see that they are not so. And what I have discovered is, once I installed clisp, it appeared in my menu (in the wrong part though, but I could correct it)! Same for uqm and jEdit.

Now the problem is... I installed jEdit with the java installer, not through the repositories... so even if I accepted that this was the solution for the other two, I do not understand it at all for jEdit. On top of that, I installed it to a different directory! Maybe because the exec script is placed to the path?

But even so, googleearth have been installed to the same directory as before, and its icon does not appear. I would settle with any explanation that makes sense, but I just can't think of one :)

---

### Post by CatKiller on 2006-10-29
> **_savior_ said:**
> I would settle with any explanation that makes sense, but I just can't think of one :)

You need to include in the .desktop file where in the menu it should appear if you want it to appear automatically, I believe. In the Categories line. So my custom "/usr/share/applications/Starcraft\ -\ Brood\ War.desktop" has the line "Categories=Application;Game;", for example. I got this from looking at the .desktop files for other applications in the menu. Perhaps the same would work for you?

Otherwise, the [Desktop Entry Specification]("http://freedesktop.org/wiki/Standards_2fdesktop_2dentry_2dspec") may be of some use.

---

