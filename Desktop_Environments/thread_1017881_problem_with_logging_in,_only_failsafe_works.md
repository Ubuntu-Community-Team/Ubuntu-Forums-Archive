---
title: "problem with logging in, only failsafe works"
date: 2008-12-21
forum: Desktop Environments
---

### Post by xc1024 on 2008-12-21
hi folks. i need your advice.

so, some time ago, i accidentally deleted my gnome. i reinstalled and had no trouble since then.

here's my problem - since the beginning of dec or so, i can't log on on gnome session other than failsafe.

my ~/.xsession-errors looks like this:
```
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found
Setting IM through im-switch for locale=pl_PL.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
Checking for nVidia: present. 
Starting Xgl with options:  -accel xv:fbo -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
xmodmap:  unable to open display ':1'

```

if it is useful in troubleshooting, i tell that i have nvidia 177 propertiary drivers and compiz.

please, i really need help.

//BTW, Merry Christmas

//EDIT: looked through Google once more. workarounds like deleting .gnome2 and .gnome1_private work, but only once.

---

### Post by xc1024 on 2008-12-23
bump

---

### Post by xc1024 on 2008-12-25
anyone?

---

### Post by xc1024 on 2008-12-31
bump

---

### Post by xc1024 on 2009-01-05
problem fixed itself, but sometimes (rarely) it appears.

---

