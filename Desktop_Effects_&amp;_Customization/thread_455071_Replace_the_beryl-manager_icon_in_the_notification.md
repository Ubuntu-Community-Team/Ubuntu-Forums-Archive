---
title: "Replace the beryl-manager icon in the notification area?"
date: 2007-05-26
forum: Desktop Effects &amp; Customization
---

### Post by toxin on 2007-05-26
Is it possible to replace the beryl-manager icon in the notification area?
I've found this [-icon-]("http://www.ambitiouslemon.com/images/icon_ruby.png") which is a bit more shiny than the default one. I understand I should place it in my icon theme folder, but what name should I give it?

Thanks.

---

### Post by ahaurw01 on 2007-05-27
Check out what this gives you:
```
locate beryl | grep icon 
```
Haven't tried changing the icon myself but I'd guess one of the things you find there is what you would need to replace.

---

### Post by toxin on 2007-05-27
Hi, thank you for your reply. I've already tried that, but the icon in the notification area seems to be hardcoded in the executable. There's a beryl-manager icon on the disk, but that only affects menus (in fact, it's the "diagonal" ruby, not the "vertical" one) :-(

Similar issue for update-manager. Damn, those icons really need to be improved... That notification area is screwing up my whole desktop appearance.  :-(

---

### Post by Mr.Black on 2007-05-27
For me the beryl-manager icon was in

/usr/share/icons/hicolor/scalable/apps

---

