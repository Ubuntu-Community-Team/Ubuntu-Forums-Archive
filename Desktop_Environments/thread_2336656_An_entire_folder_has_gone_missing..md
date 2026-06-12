---
title: "An entire folder has gone missing."
date: 2016-09-10
forum: Desktop Environments
---

### Post by pingaan on 2016-09-10
Hi,

Like the topic says. Was this logged somewhere? /var/log? Which file?

Thanks.

---

### Post by ajgreeny on 2016-09-10
I think we will not be able to help you without a lot more information.

What folder?
What have you done recently, and in particular, just before you noticed this folder was missing?
Have you looked in Trash, your users and root Trash?
If you used the terminal to delete files and folders look in **~/.bash_history** which will show all the recent commands you have used.

---

### Post by TheFu on 2016-09-10
Just restore it from the backup that was made prior to it disappearing.

BTW, I've never seen this unless the HDD was failing.  You can run fsck on the disk to see if it shows up in lost-and-found at the root of the file system.  Restoring from a backup would be the easiest answer, however.

---

