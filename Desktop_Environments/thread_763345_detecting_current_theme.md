---
title: "detecting current theme"
date: 2008-04-22
forum: Desktop Environments
---

### Post by twenty1grand on 2008-04-22
Hey there,
I was wondering if anybody knew how a non-GTK application could detect the current theme that gnome is using.

There is an environment variable called GTK_RC_FILES which points me to a file called .gtkrc-1.2-gnome2 which contains the following lines:
[FONT="Courier New"]
# Autowritten by gnome-settings-daemon. Do not edit

include "/home/my_user_name/.gtkrc.mine"[/FONT]

This file, as near as I can tell, does not exist.  I know where the themes are stored and I obviously know which theme I am using but I would like to be  able to have an application find out automatically.

Any thoughts would be greatly appreciated.

--twenty1grand

---

### Post by sdennie on 2008-04-23
For the gtk theme:
```

gconftool-2 -g /desktop/gnome/interface/gtk_theme

```

Icon theme:
```

gconftool-2 -g /desktop/gnome/interface/icon_theme

```

Window manager theme can be tricky but, assuming you are using either metacity or compiz without emerald:
```

gconftool-2 -g /apps/metacity/general/theme

```

---

### Post by twenty1grand on 2008-04-23
> **vor said:**
> For the gtk theme:
```

gconftool-2 -g /desktop/gnome/interface/gtk_theme

```

Icon theme:
```

gconftool-2 -g /desktop/gnome/interface/icon_theme

```

Window manager theme can be tricky but, assuming you are using either metacity or compiz without emerald:
```

gconftool-2 -g /apps/metacity/general/theme

```



Ok I will try that, thanks.
Que aguante San Lorenso
(I used to live in Bahia Blanca and Mar del Plata)

---

### Post by twenty1grand on 2008-04-23
> **vor said:**
> For the gtk theme:
```

gconftool-2 -g /desktop/gnome/interface/gtk_theme

```

Icon theme:
```

gconftool-2 -g /desktop/gnome/interface/icon_theme

```

Window manager theme can be tricky but, assuming you are using either metacity or compiz without emerald:
```

gconftool-2 -g /apps/metacity/general/theme

```

Just tried it, thats exactly what I needed!  I don't know why I couldn't find that out with searches.
Thanks!

---

### Post by sdennie on 2008-04-23
Glad that helped.

(And, Dale San Loren!)

---

