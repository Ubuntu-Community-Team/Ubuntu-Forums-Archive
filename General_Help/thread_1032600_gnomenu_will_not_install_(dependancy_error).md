---
title: "gnomenu will not install (dependancy error)"
date: 2009-01-06
forum: General Help
---

### Post by campbuds on 2009-01-06
I downloaded gnomenu deb file. When I try to intall the themes or the menu itself I get this...

Error: dependency is not satisfiable


I guess I should mention I never installed this before and tried following the directions, which there is really not much to anyway.

---

### Post by gettinoriginal on 2009-01-06
gnome-menu can be installed from synaptic package manager, there it will also include any dependencies.  :P

---

### Post by bwang on 2009-01-06
Which dependency is not satisfiable? I believe you have to install the gnomenu themes package before installing gnomenu.

---

### Post by campbuds on 2009-01-06
> **bwang said:**
> Which dependency is not satisfiable? I believe you have to install the gnomenu themes package before installing gnomenu.

I am actually referring to trying to install the themes package first. But then tried the menu itself and get the error then also.

---

### Post by DrDoodle on 2009-09-03
This should work:

Step 1: [Download](http://launchpad.net/gnomenu/trunk/1.9-final/+download/gnomenu-1.9.9.tar.gz) (click) Gnomenu and save it to your desktop.

Step 2: Right click and "Extract here".

Step 3: Fire up 'terminal' and run:
```
sudo apt-get install python python-xdg python-cairo python-gconf python-xlib deskbar-applet
```

Step 4: Change directory into the gnomenu dir. **cd ~/Desktop/gnomenu**

Step 5: **sudo make install**

If you require additional help, reply :)

---

