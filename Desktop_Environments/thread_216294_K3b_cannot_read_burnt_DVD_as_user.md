---
title: "K3b: cannot read burnt DVD as user"
date: 2006-07-15
forum: Desktop Environments
---

### Post by theFallen on 2006-07-15
Hi,

I burnt some DVD with K3b and then couldn't open them afterwards. Playing around I found out, that I can open them as root.
Did I do something wrong?
Is it connected to the /media folders?
Or the automount?

My user is in the following groups:
adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

CDs nevertheless are burned correctly.

---

### Post by theFallen on 2006-08-08
Someone, anyone?!?

---

### Post by clint1010 on 2006-08-08
Does the DVD automount for the user? post the contents of this file

sudo gedit /etc/fstab

---

### Post by theFallen on 2006-08-12
Thank you, that was it. The line for the DVD-Drive was missing. Why I don't know. I could swear it was there before.....???
Well, now it does work with the burnt DVD. 

Why does the automount work, when there is nothing in the fstab for this drive?

---

