---
title: "Compiz Fusion Issue"
date: 2007-10-09
forum: Desktop Effects &amp; Customization
---

### Post by brandonhaslip on 2007-10-09
I am very new to Linux. I just did a tutorial on installing Compiz, it seems to have gone off without a hitch. I can go into System>Preferences>CompizConfig Settings Manager and change settings and do all kinds of things, but when I use the keyboard shortcuts, nothing happens. It's almost like I am stuck with a "Windows Vista Basic" type of look. If anybody has any insight into this, it would be appreciated. Thanks.

Also, my system seems to be pretty locked down. I get a lot of permissions issues when editing files like xorg.conf. Is there any way around this.

---

### Post by skymera on 2007-10-09
first try emerald themes, also get beryl manager.

2 ) thats sudo, its good. it protects sensitive files

---

### Post by Whiffle on 2007-10-09
sounds like compiz isn't running.

Hit Alt+F2 and run "compiz -replace" and see if it changes anything.  That won't fix it for good but I dont' remember how to make compiz default...

---

### Post by Forlong on 2007-10-09
> **brandonhaslip said:**
> when I use the keyboard shortcuts, nothing happens. It's almost like I am stuck with a "Windows Vista Basic" type of look.
Are you running Xgl?

Then you need to choose the proper layout for your keyboard in System &#8594; Preferences &#8594; Keyboard

And about the look, try running
```
gnome-settings-daemon
```

---

### Post by indecisive on 2007-10-09
Try changing the DefaultDepth variable in /etc/X11/xorg.conf to 16.  Make sure you type *sudo nano /etc/X11/xorg.conf* to edit the file and Ctrl+X to save and leave.

---

