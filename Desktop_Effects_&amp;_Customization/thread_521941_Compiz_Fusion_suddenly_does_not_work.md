---
title: "Compiz Fusion suddenly does not work"
date: 2007-08-09
forum: Desktop Effects &amp; Customization
---

### Post by mezcla on 2007-08-09
I have had AWN + Beryl for months and more recently installed Compiz Fusion without a problem when suddenly last night my computer froze and now I can't get  compiz fusion to work.  Here is what I get when I run it in a terminal.

```
$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: present. 
Checking for Xgl: not present. 
Window manager warning: Failed to load theme "": Failed to find a valid file for theme 


(gtk-window-decorator:30005): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:30005): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:30005): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:30005): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:30005): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:30005): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:30005): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:30005): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:30005): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:30005): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:30005): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:30005): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:30005): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:30005): Wnck-WARNING **: Unhandled action type (nil)
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"



```

Any suggestions?

---

### Post by crazyhunk on 2007-08-10
install Emerald from the repos u installed Compiz Fusion and then try....

compiz --replace -c emerald &

should fix the problem

---

### Post by mezcla on 2007-08-10
That doesn't work.  Compiz is not running at all so if I try to use emerald themes I get no window borders.  This all worked fine for a while now (Compiz Fusion + Emerald) and suddenly it is broken and I'm not sure what I did to break it.  Any more suggestions?

---

### Post by ShaolinF on 2007-08-11
Same here. I don't know what I did but when I opened the terminal and typed compiz --replace it would load but give me the following error around 10 or so times: 

(emerald:28785): Wnck-WARNING **: Unhandled action type (nil)

And if I press ctrl+c the borders dissapear. Does anyone know how I can uninstall compiz and emerald ?

---

