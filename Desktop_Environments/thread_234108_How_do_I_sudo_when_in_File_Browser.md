---
title: "How do I sudo when in File Browser?"
date: 2006-08-11
forum: Desktop Environments
---

### Post by skecherkid on 2006-08-11
When I use the GNOME file browser how do I invoke sudo?  I was trying to follow some directions to install a splash image in /boot/grub/images and I created the directory using Terminal and the went downloaded a splash graphic to the Desktop and tried to use File Browser to cut it from there and paste it into /boot/grub/images   but File Browser won't let me do it.

---

### Post by maniacmusician on 2006-08-11
you have to open the file browser as sudo; meaning start it with administrative rights. Since  you're in gnome, i'll assume your file manager is nautilus. try this: in terminal, type 

gksu nautilus

hope that works for you.

---

### Post by TheEmb3rEgg on 2006-08-11
go into the terminal.
type
```
cp /source/dir/image.jpeg /target/directory/
```

EDIT: the above will work also =)

---

### Post by orb9220 on 2006-08-11
Or drag your home folder from menu down to panel so it is added there,
Then you have icon on panel for launching nautilus.

Right click properties for icon and put this in place for command
gksudo nautilus

Now you have a sudo nautilus one click away.

---

### Post by maniacmusician on 2006-08-11
^yes, this is a handy solution, but there's a reason that apps don't run in sudo by default. if you don't know what you're doing, it has the potential for disaster. should be used sparingly

---

### Post by cptnapalm on 2006-08-11
Actually, there is a deb (nautilus-actions, perhaps) in one of the *verse repositories which will let you right click in nautilus, select scripts, and choose root-nautilus.  It will open up a gksudo for you and after that, open a nautilus running as root.

---

### Post by code-breaker on 2006-08-11
> Actually, there is a deb (nautilus-actions, perhaps) in one of the *verse repositories which will let you right click in nautilus, select scripts, and choose root-nautilus. It will open up a gksudo for you and after that, open a nautilus running as root.

Automatix has something similar too (maybe the same package?). It adds 3 scripts in the right-click menu in Nautilus, including gedit-root and root-nautilus-here.

---

