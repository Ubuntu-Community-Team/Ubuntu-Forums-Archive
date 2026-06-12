---
title: "Startx Cursor"
date: 2008-08-21
forum: Desktop Environments
---

### Post by ShareBuntu on 2008-08-21
Hi,

I have GDM disabled. Whenever I login and type "startx", everything works fine except for my cursor which stays an "X" without changing to my default theme cursor. What gives?

---

### Post by kerry_s on 2008-08-21
[http://ubuntuforums.org/showthread.php?t=746374&page=3](http://ubuntuforums.org/showthread.php?t=746374&page=3)

---

### Post by ShareBuntu on 2008-08-21
> **kerry_s said:**
> [http://ubuntuforums.org/showthread.php?t=746374&page=3](http://ubuntuforums.org/showthread.php?t=746374&page=3)
Strange, my cursor is only an X when I deal with Nautilus and other Gnome applications. In Firefox, and even terminals, it's the same cursor I'm used to when launching GDM.

I noticed this before applying your solution, with no change thereafter. I did, however much earlier apply the following:

```
gconftool --type boolean --set /apps/nautilus/preferences/show_desktop false
```

I use Xmonad with Gnome.

---

### Post by ShareBuntu on 2008-08-21
Sorry to double-post, but I added the following to my .gnomerc file:

```
xsetroot -cursor_name left_ptr
```

That seems to fix it. Is "left_ptr" the default cursor used in Gnome by Ubuntu? Also, would there be a more applicable place to add the entry? Perhaps some X session configuration file?

---

