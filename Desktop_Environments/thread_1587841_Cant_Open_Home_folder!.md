---
title: "Cant Open Home folder!"
date: 2010-10-04
forum: Desktop Environments
---

### Post by mister_p_1998 on 2010-10-04
Had this problem in Lucid since day one, click on home folder, nautilus locks up and times out, I have to reboot the system sometimes twice before I can access home, although its fine in a terminal. It seems the folder .gvfs had become corrupted and I have lost all permissions to access it. After a lot of googling I found this solution which I put into a script which I can run from a terminal to fix it without rebooting. Change the username steve to your own.

sudo umount -fl /home/steve/.gvfs
sudo chown steve:steve .gvfs
rmdir .gvfs


Steve

---

