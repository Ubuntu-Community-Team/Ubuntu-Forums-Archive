---
title: "How Do I Get Back"
date: 2007-06-07
forum: Fedora/RedHat and derivatives
---

### Post by linuxlost on 2007-06-07
I have been running Fedora 7 KDE and decided to install Gnome also (via add remove software. Every thing went fine I was able to 
 log out of KDE and choose Gnome in the secion type, and it runs fine. But now if I reset sever X I end up in text based grub, and if I reboot or restat the computer I go to localhost log in .
 
 How do I get back to the desktop (graphical log in) from grub or the text based localhost log-in screen?

---

### Post by fuscia on 2007-06-07
> **linuxlost said:**
> I have been running Fedora 7 KDE and decided to install Gnome also (via add remove software. Every thing went fine I was able to 
 log out of KDE and choose Gnome in the secion type, and it runs fine. But now if I reset sever X I end up in text based grub, and if I reboot or restat the computer I go to localhost log in .
 
 How do I get back to the desktop (graphical log in) from grub or the text based localhost log-in screen?

if i understand you correctly, you need to use the *startx* command, though you would need to edit .xinitrc, first, by adding either *exec gnome-session* or *exec startkde*. is that what you're talking about?

---

### Post by vignesh on 2007-06-22
open your /etc/inittab file and scroll down to this line.

id:5:initdefault:

Here 5 tells the os to boot in runlevel 5 which in Fedora starts the login manager.If yours says 3 instead of 5 change it to 5

---

