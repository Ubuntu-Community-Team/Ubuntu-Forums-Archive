---
title: "Gnome doen't starts!!!"
date: 2005-03-15
forum: Desktop Environments
---

### Post by Skatox on 2005-03-15
Sorry for my english. I have a problem, Gnome or the Xfree86 doesn't starts  (sorry I'm  newbie), this is due to i tried to install Ati Radeons fglrx drivers but they didn't works. When Ubuntu try to enter to the graphic mode, it a appears a blue windows telling me that Xfree couldn't start. 

What i have to do?? i'm nervousus cause have some important files on ubuntu, and can't format ubuntu, cause maybe grub dissappears and can't run windows.

---

### Post by slow'puter on 2005-03-15
[QUOTE=Skatox]Sorry for my english. I have a problem, Gnome or the Xfree86 doesn't starts (sorry I'm newbie), this is due to i tried to install Ati Radeons fglrx drivers but they didn't works. When Ubuntu try to enter to the graphic mode, it a appears a blue windows telling me that Xfree couldn't start. 

What i have to do?? i'm nervousus cause have some important files on ubuntu, and can't format ubuntu, cause maybe grub dissappears and can't run windows.[/QUOTE]

As root, type:

dpkg-reconfigure xserver-xfree86

---

### Post by Skatox on 2005-03-15
I don't know why it doesn't work. It's like it wasn't installed, but it is.

What's the command for edit grub settings from the console?.

---

