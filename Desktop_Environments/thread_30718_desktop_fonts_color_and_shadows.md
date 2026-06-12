---
title: "desktop fonts: color and shadows"
date: 2005-04-29
forum: Desktop Environments
---

### Post by 23meg on 2005-04-29
simple question: how can i change the color of the fonts on the gnome desktop? the default white with drop shadows doesn't look very good on light backgrounds. also, is there a way to remove the shadows and have plain fonts?

---

### Post by Professor X on 2005-04-29
I don't think there is a simple way to do this.  There might be a gnome theme that uses color fonts.  If not, you could edit one of the existing themes.  Try googling for more info.

---

### Post by XDevHald on 2005-04-29
[QUOTE=23meg]simple question: how can i change the color of the fonts on the gnome desktop? the default white with drop shadows doesn't look very good on light backgrounds. also, is there a way to remove the shadows and have plain fonts?[/QUOTE]

To change the font of the whole desktop including taskbar, icon text, window border text and also window navigation text such as File, Edit, View, Go, Bookmarks, Tools, and Help, then you'll need configure it at [b]System > Preferences > Fonts

[/b]Now as far as the theme color font, you will need to see your .theme folder to check out how to configure this.

---

### Post by 23meg on 2005-04-30
there's no option to set colors in system / preferences / font.

and i can't seem to find a .theme folder anywhere; i do have a .themes folder, though.

---

### Post by simianMiscreant on 2005-05-14
uh yeah, i second this question. *bump*

---

### Post by Alexander Kirillov on 2005-05-14
[QUOTE=simianMiscreant]uh yeah, i second this question. *bump*[/QUOTE]
 Font color is detemined by desktop theme. Find a theme you like or  manually edit an existing theme - not for newbies. The file you need to edit is  /usr/share/themes/<themename>/gtk-2.0/gtkrc

---

### Post by denisesballs on 2005-11-08
[QUOTE=Alexander Kirillov]Font color is detemined by desktop theme. Find a theme you like or  manually edit an existing theme - not for newbies. The file you need to edit is  /usr/share/themes/<themename>/gtk-2.0/gtkrc[/QUOTE]

Which variable in the file is for the desktop font color?

---

### Post by 23meg on 2005-11-15
I've figured out how to do this and written a guide, it's [here]("http://www.ubuntuforums.org/showthread.php?t=89197").

---

