---
title: "How to exit GUI to command line to unmount partition?"
date: 2005-09-17
forum: Desktop Environments
---

### Post by helwitch on 2005-09-17
I want to entirely exit out of the GUI to the command line, but I can't figure out how to do this. I've searched the forums with dozens of different keywords, but can't figure out what command would do this.
The reason I want to do this is that I have a partition mounted to a folder on the desktop that just WILL NOT unmount. I tried umount -f, umount -l, it just won't unmount, and I suspect it's cos it's mounted to a folder on the desktop. So, I'm thinking if I was at the command line, it might unmount since the GUI wouldn't have the desktop up.
I'm rather newbie-ish, so if you've got some fabulous way for me to unmount the partition, great, but I'd still like to know how to entirely exit out of the gui to the command line, just for future reference. It's probablly really easy and I'm being all clueless in missing it, but I just can not figure it out. Thanks for any help!

---

### Post by khc on 2005-09-17
Assuming that the folder is called $DIR, you can do this from a terminal:

lsof | grep $DIR

That will tell you which application is accessing that mount point. If it's something that you don't need, you can simply kill that application.

If you really want to switch to the console, first logout, then press Ctl+Alt+1 and log in there. Use Ctl+Alt+7 to go back to the GUI.

---

### Post by Gamabunta on 2005-09-17
I think you meant Ctrl+Alt+F1 and Ctrl+Alt+F7.

---

### Post by helwitch on 2005-09-17
Lsof said it was being accessed by gam_server, which would not die, and when I googled it, apparently is part of gamin has a bug where it just will not die. But going out to the command line and unmounting the partition worked beautifully. Thanks!

---

