---
title: "Disk quota exceeded"
date: 2006-07-14
forum: Desktop Environments
---

### Post by ernel_25 on 2006-07-14
hi all, my sister tried to install a software meant for windows on my pc (running Ubuntu)in my absence.Since then I can't access ma desktop. Whenever I boot and login an error message is displayed saying disk quota exceeded and I'm asked to shut down or reboot.I actually didn't have much disk space left b4 my sista installed the damn software .... So how can I overcome this problem ???? Is there a way I could delete some files to free some disk space

---

### Post by OpsVentus on 2006-07-14
You can try to use the fail safe boot, this will take you to the terminal. There you can look around and delete file's.

When you get to the terminal after logging in you will be in your home directory.
There you can type 'ls' this will list the files in that directory.
With 'rm 'filename'' you can remove file's.
Untill you got enough space to log back in.

Good luck,
Bart.

---

### Post by Sendervictorius on 2006-07-14
Or you could boot from a live CD, mount the drives, and delete away!

---

### Post by swamytk on 2006-07-14
> **ernel_25 said:**
>  I can't access ma desktop. Whenever I boot and login an error message is displayed saying disk quota exceeded and 

One more solution, If you have set root password:
Dont' Login into Desktop screen. Press Ctrl+Alt+1. it will take u to console. Login as root. go to ur home directory and delete the unwanted files.

---

### Post by OpsVentus on 2006-07-14
You do not have to be root do delete file's from your home-dir.
If you don't have to be root, don't! unless you understand very very well what your doing!
What swamytk said about 'Ctrl+Alt+1' to take you to the terminal is ok, but you do not need to login as root.

---

