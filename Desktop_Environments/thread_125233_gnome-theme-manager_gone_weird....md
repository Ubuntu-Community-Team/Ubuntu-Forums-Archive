---
title: "gnome-theme-manager gone weird..."
date: 2006-02-03
forum: Desktop Environments
---

### Post by kjempe on 2006-02-03
Folks,

since recently I`m no longer able to change the looks of applications run with sudo. The only thing I did today was installing tor and privoxy to surf anonymously (using these instructions: [http://ubuntuforums.org/showthread.php?t=10825&]("http://ubuntuforums.org/showthread.php?t=10825&")) and speeding up the booting process, first with InitNG ([http://ubuntuforums.org/showthread.php?t=80423&]("http://ubuntuforums.org/showthread.php?t=80423&")), then with sysv-rc-conf ([http://ubuntuforums.org/showthread.php?t=89491&]("http://ubuntuforums.org/showthread.php?t=89491&")).

When I start gnome-theme-manager, I get the following message in my terminal (with or without sudo):

```
(gnome-theme-manager:9152): Gtk-CRITICAL **: gtk_icon_info_get_filename: asserti on `icon_info != NULL' failed

(gnome-theme-manager:9152): Gtk-CRITICAL **: gtk_icon_info_free: assertion `icon _info != NULL' failed

```

When I start the manager with sudo, I`m still able to install and choose GTK, metacity and icon themes but they won`t apply to "reality", only to the preview inside the manager. When I`m accessing the folder that`s holding the theme-files (via gnome-theme-manager), I`m getting the following:

```
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice

--- Hash table keys for warning below:
--> file:///root

(nautilus:9189): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

--- Hash table keys for warning below:
--> file:///root

(nautilus:9189): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)
```

Does anybody have a clue what`s going on here and how it could possibly be solved? I`d appreciate any suggestion.

---

### Post by syklitengutt on 2006-02-03
have you tried booting without initNG?
I got allot of strange behavor when booting from initNG

---

### Post by kjempe on 2006-02-03
[QUOTE=syklitengutt]have you tried booting without initNG?
I got allot of strange behavor when booting from initNG[/QUOTE]

I actually uninstalled InitNG quite quickly because it didn`t work out so well. I erased it`s lines from the menu.lst and as far as I understood the how-to, I didn`t change anything else. So how comes it`s irritating the theme-manager? I don`t get silly error-messages running any other administrative software via sudo on my machine. But, when I run gnome-theme-manager as as user, I get the same output, except for the latter.
I just thought that it possibly relates to me messing around with the icons recently. I customized a Tango set pretty much so maybe I crashed some important system icon.

---

