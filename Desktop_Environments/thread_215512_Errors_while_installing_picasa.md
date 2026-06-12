---
title: "Errors while installing picasa"
date: 2006-07-14
forum: Desktop Environments
---

### Post by abhiomkar on 2006-07-14
I have downloaded picasa for linux from [http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_2.2.2820-5_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_2.2.2820-5_i386.deb)

When i tried to install it, this was the error message ...

$ sudo dpkg -i picasa_2.2.2820-5_i386.deb
(Reading database ... 112083 files and directories currently installed.)
Unpacking picasa (from picasa_2.2.2820-5_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing picasa_2.2.2820-5_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./opt/picasa/lib/libfreetype.so.6.3.8')
Errors were encountered while processing:
 picasa_2.2.2820-5_i386.deb

Whats went wrong. Any suggestions...

---

### Post by philippe_carlo on 2006-07-14
I installed the exact same version without any problems. Maybe something went wrong during the download of the package? Try downloading it again. Also make sure you have enough disk space available in /var.

---

### Post by ChrisDerson on 2006-07-14
I also managed to get picasa running on two different PCs without problem.  The 'short read' suggests to me that the picasa .deb file didn't download correctly.  You should try grabbing it again.  When you have, post the exact file size in bytes, and the MD5 checksum if you can, here so they can be checked.
At least you'll then know the .deb file is Ok.

---

### Post by abhiomkar on 2006-07-14
> **philippe_carlo said:**
> I installed the exact same version without any problems. Maybe something went wrong during the download of the package? Try downloading it again. Also make sure you have enough disk space available in /var.

Yes, i downloaded it again, and tried to install . It is working now.
It is successfully installed.
Thanku

---

