---
title: "Mounted media not appearing on desktop."
date: 2009-02-23
forum: General Help
---

### Post by JaredFactley on 2009-02-23
Whenever I plugged in an external harddrive/camera/PSP etc. it used to appear on the desktop.

Now for some reason they do not appear. They still mount, I just have to go into the Places menu to open them.

I don't remember turning off any option at all. Is there a way I can get them back?

---

### Post by ibuclaw on 2009-02-23
Press **Alt+F2** and type in
```
gconf-editor
```
Enter the following subdirectories:
**apps / nautilus / desktop**

and locate the **volumes_visible** key and check it.
Mounted volumes should now appear on your desktop.

If you are carrying out tasks such as this on the odd basis, you may be interested in looking up/installing Ubuntu-Tweak, an application that makes simple gnome tweaks (including the one that you have just asked about now) even easier. It is in my personal opinion very recommended for the new beginners.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Regards
Iain

---

### Post by JaredFactley on 2009-02-24
Perfect, thanks a lot. Never thought to look there.

And thanks for the advice, I'll look into it.

---

