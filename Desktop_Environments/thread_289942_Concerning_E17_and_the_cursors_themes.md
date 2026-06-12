---
title: "Concerning E17 and the cursors themes"
date: 2006-10-31
forum: Desktop Environments
---

### Post by daedalusman on 2006-10-31
I'm using e17 and was wondering if there is a way to get firefox and thunderbird to use the e17 cursor theme instead of the xcursor theme? I would like the cursor to be uniform throughout. This is on edgy. So can anyone help out here, thanks.

---

### Post by daedalusman on 2006-11-03
Well just in case anybody else is interested I came across this just now.

> E17 pointer for GTK/QT applications
07.10.2006 - 02:58
Currently i'm trying to track down how the x cursor theming works. I want to patch the e17 mouse cursor dialog so that it also theme the xorg cursor.

For now this works following these few steps:
1. Download this theme package.
2. Create the dir ~/.icons .
3. Extract the theme using tar xfvj enlightenment_xorg_pointer.tar.bz2 -C ~/.icons/ .
4. Create the file ~/.Xdefaults and add these line:
   Xcursor.theme: enlightenment
5. Restart your X.

Hope you like it! :)

From this website...

[http://omicron.homeip.net/](http://omicron.homeip.net/)

Hopefully they will figure it out in a less hackish way but this will do just fine for now.

---

