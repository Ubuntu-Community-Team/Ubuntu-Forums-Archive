---
title: "Locales. ???"
date: 2006-03-06
forum: Desktop Environments
---

### Post by xmastree on 2006-03-06
Can somebody please explain, or point me to an explanation. Just what exactly **is** a locale? And why do I get an error whenever I try to run something from a console?
```
chris@xmastree:~$ gedit

(gedit:14399): Gdk-WARNING **: locale not supported by Xlib

(gedit:14399): Gdk-WARNING **: cannot set locale modifiers
chris@xmastree:~$

```The app always works fine, but I just don't like seeing these errors, it looks bad. I've had them with all three ubuntu distros.

---

### Post by Xian on 2006-03-07
X11 has its own locale system that is almost-but-not-entirely compatible with glibc locales. 
Try installing the xorg-build-macros package.

---

### Post by xmastree on 2006-03-07
[QUOTE=Xian]Try installing the xorg-build-macros package.[/QUOTE]Yep! That worked. :D

Not sure how, but it did.

Thanks.

---

### Post by Xian on 2006-03-07
[QUOTE=xmastree]Not sure how, but it did.
[/QUOTE]

Alot of people say that about my explanations. :)
You can get info about that pkg at the Ubuntu Packages site.

---

