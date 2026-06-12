---
title: "editing the Grub"
date: 2005-11-24
forum: Desktop Environments
---

### Post by majoneza on 2005-11-24
Hello!
I'm trying to edit my Grub (menu.lst), so Windows XP boots for default. I know how to do this, but I can't realy edit the stuff, becaouse when I open "menu.lst" it displays as "read only". What do I have to do to get full permission to edit? :confused:

---

### Post by Leif on 2005-11-24
use sudo. as in, instead of "gedit menu.lst", do "sudo gedit menu.lst"

---

### Post by sunshinerecorder on 2005-11-24
You have to open this file as root. Just type "sudo gedit /boot/grub/menu.lst" into a terminal.

---

### Post by _4ace on 2005-11-24
Or if you are a linux rookie like myself. run nautilus as root, find and open your file and work your magic.

---

### Post by aysiu on 2005-11-24
[QUOTE=_4ace]Or if you are a linux rookie like myself. run nautilus as root, find and open your file and work your magic.[/QUOTE] By the way, to do this properly, run the command ```
gksudo nautilus
```

---

