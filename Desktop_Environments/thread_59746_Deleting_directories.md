---
title: "Deleting directories"
date: 2005-08-25
forum: Desktop Environments
---

### Post by itsmeagain on 2005-08-25
Hi 
I've made a directory using the command ' sudo mkdir /mnt/winslave', But how can  delete this directory. If I try to dump it in the Wastebasket it does not allow me to do it.

Thanks

---

### Post by GeirG on 2005-08-25
First: If there was any more specific error messages, please remember to include those next time you post a question. Any details makes it easier for us to help you.

Knowing only that you are "not allowed" to dump the dir in the Wastbasket, I would say the most likely cause is that you do not have the necessary permissions.

When creating the dir using sudo, the dir is created and owned by root (This is what sudo does, it gives you temporary superuser/root/God powers).
When you try to delete the dir using from Nautilus (dragging it to the Wastebasket or otherwise...) you are operating as a normal user, without the necessary permissions to delete files/dirs created/owned by root. This is as it should be.

I believe opening a terminal and issueing the following command should do the trick:
# sudo rmdir /mnt/winslave
... if the dir is empty, if not use:
# sudo rm -rf /mnt/winslave
... for a forced, recursive delete (i.e. the dir and everything in it).

Do some googling or read a "Starting with Linux/Unix" book to get som info on basic permissions. It will keep you from a lot of headaches in the future. It's not too complicated, but really helpfull.

Regards,

---

### Post by matej on 2005-08-25
[QUOTE=itsmeagain]Hi 
I've made a directory using the command ' sudo mkdir /mnt/winslave', But how can  delete this directory. If I try to dump it in the Wastebasket it does not allow me to do it.

Thanks[/QUOTE]
 sudo rm -r /mnt/winslave

(and it have to be unmounted: sudo umount /mnt/winslave)

---

### Post by itsmeagain on 2005-08-25
Thanks for the info it worked fine

---

