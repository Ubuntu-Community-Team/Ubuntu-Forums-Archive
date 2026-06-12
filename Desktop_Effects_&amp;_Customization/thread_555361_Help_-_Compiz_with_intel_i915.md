---
title: "Help - Compiz with intel i915"
date: 2007-09-20
forum: Desktop Effects &amp; Customization
---

### Post by kevdog on 2007-09-20
Just did fresh feisty install on Laptop with Intel 82830 CGC with the i915 driver loaded -- although the xorg.conf file states the i810 driver.

Im trying to enable compiz (compiz/fusion/beryl???) and used these instructions:
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)


The instructions seemed fairly straightforward, however nothing happened when did the compiz --replace command, other than losing the tops, and having to reboot.

Has anyone gotten this with the i915 driver??  Google is not the best resource since it talks about a bunch of things I didnt do or not pertinent to my situation.

Thanks for any input.

---

### Post by ryno519 on 2007-09-20
Try running this command.

```
compiz --replace -c emerald &
```

---

### Post by kevdog on 2007-09-20
Can you guide me a little bit more -- I just removed all the packages that were installed by the above tutorial.  Where do I start, and what do I need to install?

---

### Post by kevdog on 2007-09-20
That sucked using 
compiz --replace -c emerald &

Now all the tops are gone and I cant switch with the Alt-Tab button.  Im going to have to log out since I cant minimize or close any window now.

What else can I try????

---

### Post by kevdog on 2007-09-20
I finally got the top problems solved by modifiying the xorg.conf file, but when trying to run compiz I get the following:

sudarshan@Sudarshan:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 

(gtk-window-decorator:5515): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5515): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5515): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5515): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5515): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5515): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5515): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5515): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5515): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5515): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

Help??

---

