---
title: "trouble with compiz in feisty"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by DOH on 2007-10-19
this is the output I get when i run compiz in terminal.
```

Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:8545): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8545): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by kevmaster on 2007-10-19
What if you press **ALT**+**F2**, type ```
compiz --replace
``` and press **Run** ?

---

### Post by DOH on 2007-10-19
this is what i get when i run compiz --replace in terminal

```

Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9493): Wnck-WARNING **: Unhandled action type (nil)
Segmentation fault (core dumped)

```

---

### Post by kevmaster on 2007-10-20
Yeah but what if you press **ALT+F2,**+**F2** and run it. Instead of the terminal

---

