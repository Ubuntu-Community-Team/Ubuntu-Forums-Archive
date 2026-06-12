---
title: "LinPopUp and other older apps look bad in xfce"
date: 2008-12-21
forum: Desktop Environments
---

### Post by wriggary on 2008-12-21
Hi everyone, back again!

This time, I have a rather interesting problem that I can't seem to properly google for.  Whenever I run linpopup (apt-gotten from the ubuntu repos) it squeezes all the letters in the menus and status bar, but thankfully not the message itself, making the program still usable but ugly.  see screenshot. 

(thats tilda transparencied to the background, and conky on the bottom right... you may notice that i'm using 8.04... the 2.6.24 kernels seem to work better for me. backports are enabled, though)

Anyone know how to fix?

thanks in advance!

---

### Post by watchitman on 2008-12-22
Looks like you have an old GTK 1.x app there. GTK 1.x is *really* old (going on 6 years since GTK 2.x was introduced), out of date and no one uses it. You should find a modern GTK+ app that gives you the same functionality, if you want pretty fonts.

---

### Post by kerry_s on 2008-12-22
it just looks like you need to set the font for gtk1 programs. i think the manual way is to create a .gtkrc file and put something like this:

```
style "gtk-default" {
fontset = "-adobe-helvetica-medium-r-normal--9-*-*-*-*-*-*-*"
}
class "GtkWidget" style "gtk-default"
```

just do a little googling, i'm not sure if there's a gui program to do it anymore.

gtk1 programs are being dropped from the repo's all the time, i also recommend you find a gtk2 alternative and try not using any gtk1 programs.

---

### Post by x1a4 on 2008-12-22
Use /usr/bin/switch to change GTK1 themes.

---

