---
title: "Larger cursor on a notebook??"
date: 2008-08-04
forum: Desktop Environments
---

### Post by windyweather on 2008-08-04
8.04 - 
I'd like to use a larger cursor.

Tried to install and use gcursor, but it doesn't seem to do anything. I tried to set the cursor size larger [32] and then hit INSTALL THEME no change. Even after a relog or restart.

Got a pointer to how to change the size of the cursor?

btw, here's what I get when I try to use gcursor:
> darrell@Tornado:~$ gksudo gcursor
(gcursor:5801): libglade-WARNING **: could not find signal handler 'open_theme_dir'.
(gcursor:5801): libglade-WARNING **: could not find signal handler 'entry_selected'.
(gcursor:5801): libglade-WARNING **: could not find signal handler 'size_changed'.
darrell@Tornado:~$ 



Thanks,
- windy

---

### Post by Vadi on 2008-08-04
I know that some themes have a larger cursor. But I forgot the name of it... it was comic something.

---

### Post by chunchengch on 2008-08-05
There are variable sizes and colors in comixcursors, you can install it from Synaptic.

[COLOR="Red"]$ sudo apt-get install comixcursors[/COLOR]

---

### Post by kerry_s on 2008-08-05
i use the crystal cursors.

```
sudo apt-get install crystalcursors
```

the just go to desktop> preferences> mouse
and select a large 1 in the color you want, with or without animation.

there's also bigcursor if you like a simple default cursor but bigger, it's in the repo.

---

### Post by kirsis on 2008-08-05
You don't actually have to install anything.

Just go to System->Prefs->Appearance

Click Customize (on the Theme tab)

Choose the Pointer tab

Choose the DMZ_White pointer

Use the slider to adjust size accordingly.

Voila :)

---

### Post by windyweather on 2008-08-05
> **kirsis said:**
> You don't actually have to install anything.

Just go to System->Prefs->Appearance
Click Customize (on the Theme tab)
Choose the Pointer tab
Choose the DMZ_White pointer
Use the slider to adjust size accordingly.
Voila :)

That's got it... thanks...

For some reason the mouse or cursor prefs don't work.
- windy

---

### Post by kerry_s on 2008-08-06
> **kirsis said:**
> You don't actually have to install anything.

Just go to System->Prefs->Appearance

Click Customize (on the Theme tab)

Choose the Pointer tab

Choose the DMZ_White pointer

Use the slider to adjust size accordingly.

Voila :)

hmm, i don't have that in etch debian gnome. :confused:

---

### Post by Vadi on 2008-08-06
Maybe because it's a different OS? :/

---

### Post by kerry_s on 2008-08-06
> **Vadi said:**
> Maybe because it's a different OS? :/

:lolflag: yeah, it must be a ubuntu tweak or just a new setting in the newer gnome version.
etch is using a older version, 2.14.3

---

