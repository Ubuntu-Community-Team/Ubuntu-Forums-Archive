---
title: "Creating a launcher for run (alt+f2)"
date: 2009-03-05
forum: General Help
---

### Post by Ms_Angel_D on 2009-03-05
This one has me stumped, does anyone know what command is used to create a launcher for run (eg. alt+f2)? I want to make .desktop file for use with Ubuntu-system-panel's compact list.

Thanks in advance,
Angel

---

### Post by mcduck on 2009-03-05
I can't check if if this is correct, but if I remember right the program that runs when you press Alt-F2 is "gnome-open".

edit: nope, it's not. Might just be a part of the gnome-panel, as the shortcut doesn't work if the panel is not running.

---

### Post by Ms_Angel_D on 2009-03-05
Hi Mcduck thanks for the reply but unfortunatly that doesn't seem to work. I also tried it in terminal and got this:

```
angel@angel-desktop:~$ gnome-open
Usage: gnome-open <url>
angel@angel-desktop:~$ 
```

---

### Post by mb_webguy on 2009-03-05
The gnome-open command opens a file or directory using the Gnome default application for that type of file.  I don't think it has much to do with the Alt+F2 run dialog.

While [this]("http://www.ubuntugeek.com/gmrun-substitute-for-gnome-run-dialog-in-ubuntu.html") isn't the actual Gnome run dialog, you might find it helpful.  I have an Openbox/PyPanel session, and use it as a drop-in replacement for the Gnome run dialog.

---

