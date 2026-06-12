---
title: "How to have desktop display contents of HOME directory?"
date: 2010-05-24
forum: Desktop Environments
---

### Post by bunburya on 2010-05-24
Hi, I am just coming to GNOME from KDE where I used the folder view desktop widget to display the contents of ~ directory (/home/<user>) rather than the "Desktop" directory itself, as that's where all the stuff I wanted to access from the desktop was. Is there any way I can do this in GNOME with the actual desktop (as opposed to a widget)?

Thanks.

---

### Post by kerry_s on 2010-05-24
look in gconf-editor, i think i saw a setting for that, try using the search in there.

---

### Post by sidewalkcynic on 2010-05-24
terminal:    gconf-editor

apps
   nautilus
      preferences

         [strike]show desktop[/strike]

my bad

---

### Post by posburn on 2010-05-24
Actually, its:

```
gconf-editor
```

then go to:

apps
nautilus
preferences
and check the box for desktop_is_home_dir

---

### Post by bunburya on 2010-05-24
Thanks guys :D I actually did it by deleting my Desktop folder but I guess the gconf way is the safer way.

---

