---
title: "changing keyboard layout in KDM"
date: 2008-08-22
forum: Desktop Environments
---

### Post by gefenm11 on 2008-08-22
my layout is configured in xorg.conf
Option "XkbLayout" "us,ru"

i use kkbswitch to change layouts, and i did not configure any shortcut for changing layouts, other then the shortcuts given by kkbswitch

if i lock the desktop, and my layout is not us, i'm unable to type my password because the layout is wrong, and there is no way to change it.

is there a way to change layout from the unlock screen (like it exists in gdm)?

---

### Post by der_joachim on 2008-08-23
You can configure xorg to switch layouts on the fly by pressing Alt+Shift. In your keyboard section of /etc/X11/xorg.conf, just add the following line:

```

Option "XkbOptions" "grp:alt_shift_toggle"

```

If you already have any XkbOptions configured, you can append them with commas.

---

### Post by gefenm11 on 2008-08-23
i am aware of this solution, but i wonder if there is a solution similar to what is done in GDM (providing a button that will allow to change the layout) so that i will have visual information of the current layout, considering that i don't see what i type in the password field.

---

### Post by der_joachim on 2008-08-24
If there is one, I am not aware of it. I'll keep an eye on this thread since I would be happy for a solution as well.

---

### Post by gefenm11 on 2008-09-18
update:
1. enabling keyboard layouts in System Settings (3.5.10) will also enable the language indicator in the lock screen, but then the xorg.conf settings will be overwritten with the KDE settings (and kkbdswich will be useless)
2. in kde 4.1 (whatever is in interpid alpha 4 CD) it is possible to enable the language indicator WITHOUT enabling KDE language management (xorg.conf is setting the layouts, and KDE only show the current) will add the language indicator to lock screen.

---

