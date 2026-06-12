---
title: "rox-filer/xfce customization"
date: 2006-03-20
forum: Desktop Environments
---

### Post by bionnaki on 2006-03-20
I recently put xfce on my friend's slower machine. so far so good. a few questions though.

- how to configure rox-filer to always stay the same size or at least not open so small?

- how do you utilize the desktop? I'd like to put icons linking to his home, firefox, media player, etc?

---

### Post by az on 2006-03-20
[QUOTE=bionnaki]I recently put xfce on my friend's slower machine. so far so good. a few questions though.

- how to configure rox-filer to always stay the same size or at least not open so small??[/QUOTE]

I forget, but it is one of the preferences options.

[QUOTE=bionnaki]
- how do you utilize the desktop? I'd like to put icons linking to his home, firefox, media player, etc?[/QUOTE]

Use the pinboard option.  Launch rox with -p=1 (or any other number, you can have several different pinboards)

rox -p=1

---

### Post by bionnaki on 2006-03-20
thanks - ok, whats the pinboard option? how do you do that?

also, I have included the taskbar to the xfce bottom panel. how can I get rid of the top default taskbar?

---

### Post by Beowolf on 2006-03-20
[QUOTE=bionnaki]thanks - ok, whats the pinboard option? how do you do that?

also, I have included the taskbar to the xfce bottom panel. how can I get rid of the top default taskbar?[/QUOTE]

If you run the command 
```
rox -p=anythingyouwanthere
```
rox will take control of your desktop, where you can just drag and drop icons from any rox window. My personal experience is that once you use the pinboard, rox-filer gets even faster. If you use this to draw your desktop you might want to kill xfdesktop4 since it would be lying idle in the background and using resources.

Yuo can get rid of the taskbar by 
```
killall xftaskbar4
```
which would kill it rightaway. You can always use the taskbar plugin for the xfce-panel.

For the resizing problem, in the options menu for rox-filer, you choose "never automatically resize windows" option. And by the help of "inherit parent window properties", you can right click and save the display properties such as the window size/position of a given directory, say your home directory.

---

### Post by bionnaki on 2006-03-20
works! thanks

now, another question. how can I set up desktop icons?

---

### Post by az on 2006-03-20
Everything on the pinboard is a symlink to the actual thing, which is different than a "real" desktop which is it's own folder.

You drag and drop icons onto you desktop/pinboard.

---

### Post by bionnaki on 2006-03-20
ok. not sure what that means...

is there anyway to get a full utilization of the desktop?

---

### Post by az on 2006-03-20
[QUOTE=bionnaki]ok. not sure what that means...

is there anyway to get a full utilization of the desktop?[/QUOTE]
Sorry about the typo  ("symling" should have been "symlink" which is a shortcut.  I often type wearing latex gloves on a laptop covered in plastic.  I work in an operating room...)

No, rox does not provide a desktop like Gnome or KDE.

---

### Post by bionnaki on 2006-03-20
ok. so, there's no possible way in xfce to get a desktop? thats weird...

---

### Post by az on 2006-03-20
Icewm, fluxbox, and most other window mangers do not provide a desktop.  Actually, in Gnome, it is nautilus that provides the desktop.  In kde, you cannot install kdestop without install konqueror.

There are other desktop icon packages available, but they all suck more than using the rox pinboard.  

If you think about it, you don't really need a desktop.  I ran icewm for years without using a desktop as a folder.

---

### Post by bionnaki on 2006-03-20
ok gotcha - thanks

---

