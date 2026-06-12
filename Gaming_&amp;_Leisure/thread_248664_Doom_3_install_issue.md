---
title: "Doom 3 install issue"
date: 2006-09-01
forum: Gaming &amp; Leisure
---

### Post by Cable on 2006-09-01
I'm trying to run the Linux Doom 3 installer (doom3-linux-1.3.1302.x86.run).  When I run it, the terminal outputs this...
```

Verifying archive integrity... All good.
Uncompressing DOOM III.......................................................... ..................................

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",
Running setup as user

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

``` But it still opens up the window asking for root permissions.  However, when I type in the root password and press enter, it just pops up again.  To get it to go to the next window I have to hit cancel.  Also, both windows that pop up are *extremely* hard to read.  Attached is a screenshot of each window.  How do I fix these problems?

---

### Post by Cable on 2006-09-01
Nevermind...refer to my first post.

---

### Post by justin whitaker on 2006-09-01
The doom installer wants to save the game to /usr/local/games, which generally ubuntu users do not have permissions for. 

Change the folder reference to something like /home/doom and you should be fine.

---

### Post by Ptero-4 on 2006-09-01
You need to use the password of the user account you created when you install ubuntu.

---

### Post by Cable on 2006-09-01
> **Ptero-4 said:**
> You need to use the password of the user account you created when you install ubuntu.
 
Indeed, and that is exactly what I've been trying to do.  This is the only program that asks for administrative privileges that is having this problem.  Everything else works perfectly fine.

---

### Post by Ptero-4 on 2006-09-04
the problem may be that the Doom installer tries to use su to do the authentication. That command requires a root password, but ubuntu's root account is disabled by default (as a safety measure), instead it uses sudo to do the authentication (this explains why the doom installer fails whereas everything else works). The solution is this. In a console type:
```

sudo -s -H

```
Put your admin paasword. The shell will change to the root shell, from here you just need to run the doom installer as usual. It should recognize that you're in a root shell and install straight away.

---

### Post by DoktorSeven on 2006-09-04
Better yet, run it with **gksudo**, the sudo command made for running GUI apps as root.

**gksudo ./doom3-linux-1.3.1302.x86.run**

(if you're running KDE/kubuntu, there's a different command: kdesu or something similar.)

---

