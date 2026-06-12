---
title: "Ugly Black Window Borders or No Title Bar"
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by jader2toesbumpy on 2007-11-11
I just installed compizfusion and everything is running fine except this one problem.  I have the chose between these ugly and distracting black borders around my windows or I have no tittle bar. On ccsm if I enable windows decoration I get the black windows, if I uncheck it I get no tittle bar. Please help below are attached pictures of the problem I am describing.

devin@devin:~$ compiz --replace | tee output.txt &
[1] 7528
devin@devin:~$ Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7552): Wnck-WARNING **: Unhandled action type (nil)


thank you in advance.

---

### Post by qamelian on 2007-11-11
That doesn't look like a window border. It looks more like a really poorly configured drop-shadow. I think you need to adjust the settings for the shadow to fix this up. I know where to fix this for an emerald them, but I'm not sure where the shadow settings are for the gtk-window-decorator.

EDIT: I should have looked closer at the other attachment.:o)
Try reducing the shadow radius, and maybe reduce the shadow opacity just a bit.

---

### Post by jader2toesbumpy on 2007-11-11
i have tried that but no configurations I do in the window decorations apply

---

### Post by jader2toesbumpy on 2007-11-12
I dont know how or why this worked but it did.  Ok in CCSM click on preferences and change the back end from flat-file to gconf and then back to flat file and it worked.

---

