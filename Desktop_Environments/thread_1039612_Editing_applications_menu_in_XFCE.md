---
title: "Editing applications menu in XFCE?"
date: 2009-01-14
forum: Desktop Environments
---

### Post by MisterFlibble84 on 2009-01-14
I've searched the forums for this but didn't find an answer that works.

How do I add or remove shortcuts to the Applications panel  manually?

Thanks!

---

### Post by adamlau on 2009-01-14
```
cp ~/.cache/xfce4/desktop/menu-cache--etc-xdg-xfce4-desktop-menu.xml.xml ~/.config/xfce4/desktop/menu.xml
```

Edit menu.xml accordingly.

---

### Post by MisterFlibble84 on 2009-01-14
Grrrr, they took away the Thank You ribbon.

Well, here's an imaginary one.

Thanks! :popcorn:

---

### Post by c0rv1d on 2009-01-15
By the way, if you want to edit the "system" menu, there are two places to look

Globally: /usr/share/applications/
Locally: ~/.local/share/applications/

within these directories there are .desktop files that describe menu items individually. According to whether the file exists in abovementioned directories (and sub directories thereof) and its contents, it will produce an item to be added to the system menu. I usualy cp an existing .desktop file and use it as a template to modify its contents to add new items.

I don't know why they didn't just create a proper GUI or integrated the system menu in the standard menu editor...

Cheers

---

### Post by Falcon1002 on 2009-01-16
Thanks a lot! I now know how to get my menu items where I want them!:)

---

