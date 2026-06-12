---
title: "fonts in Xubuntu"
date: 2008-06-20
forum: Desktop Environments
---

### Post by nkessler2000 on 2008-06-20
I've been using Xubuntu for a while, but one thing has been bugging me and that's the unbelievably huge fonts used. It's obnoxious and somewhat inconsistent as not every app suffers from gigantic fonts.

The default font is Sans 7 with default DPI

see screenshot for example.

[IMG]http://img514.imageshack.us/img514/5401/wtfqu1.jpg[/IMG]

Also what's up with the blank space in the System Notification area on the taskbar? Right now it's only a small blank space but sometimes it expands to a very large blank space. see pic

[IMG]http://img385.imageshack.us/img385/7576/whyvk9.jpg[/IMG]

any ideas?

---

### Post by kerry_s on 2008-06-20
doesn't mplayer have it's own settings for fonts?
is there anything in the space, i've seen that when the theme didn't have a icon for the program, try clicking in the space.

---

### Post by nkessler2000 on 2008-06-20
> **kerry_s said:**
> doesn't mplayer have it's own settings for fonts?
is there anything in the space, i've seen that when the theme didn't have a icon for the program, try clicking in the space.

SMPlayer is a QT program, but the font problem also affects GTK programs. Firefox is probably the worst offender

and no, when I left or right click on the space, there's nothing there

---

### Post by kerry_s on 2008-06-20
oh, it's qt:
sudo apt-get install qt3-config
(or qt4-config, if its using that version)

that can be used to set all qt options.

---

### Post by nkessler2000 on 2008-06-21
> **kerry_s said:**
> oh, it's qt:
sudo apt-get install qt3-config
(or qt4-config, if its using that version)

that can be used to set all qt options.

thanks! that worked for QT. firefox is still messed up though. oh well

[IMG]http://img295.imageshack.us/img295/8125/ffty8.jpg[/IMG]

---

### Post by kerry_s on 2008-06-21
okay for firefox try this, type->
```
about:config
```

in the filter: dpi
set that to 96

---

### Post by nkessler2000 on 2008-06-21
> **kerry_s said:**
> okay for firefox try this, type->
```
about:config
```

in the filter: dpi
set that to 96

Hey that worked! Thanks for your help.

---

