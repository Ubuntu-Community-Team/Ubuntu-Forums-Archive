---
title: "Would like to change default behaviour of Sound Juicer + Gnome integration"
date: 2006-08-13
forum: Desktop Environments
---

### Post by lioncoeur on 2006-08-13
Hi there,

Default behaviour when you open an audio CD which has just been mounted is to start up Sound Juicer. This is okay normally, but some of my CDs have CD-rom content as well which I can't figure out how to access. When I right-click on the CD-rom icon on my desktop I get the options "Open" and "Browse Folder", both of which open Sound Juicer.

I know sudo apt-get remove sound-juicer will work, but I kind of like the program :P

Thanks!

---

### Post by Ahriman on 2006-08-13
If you go to System -> Preferences and open "Removable Drives and Media", then click on the Multimedia tab at the top, you can change the default behavior for when an audio CD is inserted.

ie. If you want to have nautilus open a window straight away, you could type in there: nautilus /mnt/cdrom0 (if your cdrom is mounted to /mnt/cdrom0)

---

