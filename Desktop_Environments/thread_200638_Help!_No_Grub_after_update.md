---
title: "Help! No Grub after update"
date: 2006-06-20
forum: Desktop Environments
---

### Post by stevetxt on 2006-06-20
I did apt-get update/upgrade today and now can not get back in to my laptop system at all.  When I power on, it gets as far as the following:

GRUB Loading stage 1.5

GRUB Loading, please wait...

Error 18

That's it, no more.  What can I do to straighten this out?

---

### Post by Isoss on 2006-06-20
Hope this would help:
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+missing](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+missing)

---

### Post by stevetxt on 2006-06-20
Thanks everyone!  I've got Grub restored now.  I used the second entry on the link above, which I've copied here in case anyone has a similar problem.  I may have typed "sudo grub" instead of grub, if that makes any difference when using the Ubuntu Live CD.

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

---

