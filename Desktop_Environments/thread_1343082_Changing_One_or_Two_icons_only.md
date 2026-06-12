---
title: "Changing One or Two icons only"
date: 2009-12-01
forum: Desktop Environments
---

### Post by zootoxin on 2009-12-01
I have a really nice icon set installed at the moment, but there are a couple of things would like to change. 

Firstly the icons in the notification section. Possible?

And then I would like to change a couple of icons from this set to different ones either homemade or from another set.

Possible?

If so how.

Thanks 

Zoot

---

### Post by doas777 on 2009-12-01
well, icons are bound to buttons based on name. the trick is the find the current icon for that button. make note of it's original name, and rename it to somthing else.
then add your new icon to the same folder, and rename it to the original name.

icons are usually in /usr/share/icons/<themename>/
or can be in ~/.icons

---

### Post by zootoxin on 2009-12-03
> **doas777 said:**
> well, icons are bound to buttons based on name. the trick is the find the current icon for that button. make note of it's original name, and rename it to somthing else.
then add your new icon to the same folder, and rename it to the original name.

icons are usually in /usr/share/icons/<themename>/
or can be in ~/.icons


Worked a treat thanks

---

### Post by gadolinio on 2009-12-03
You'll find installed incon themes in /usr/share/icons  and in /home/your_user_name/.icons.
Inside each icon folder you'll find almost every icon used by your computer (not openoffice's, for example). Change everything you want, though it may be somewhat tiring... Remember that files inside /usr/share/icons cannot be modified unless you're the root user. You can copy the icon folder to /home/your_user_name/.icons, and modify it there.

---

