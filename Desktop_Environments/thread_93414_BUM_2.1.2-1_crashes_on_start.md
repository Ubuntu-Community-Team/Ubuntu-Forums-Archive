---
title: "BUM 2.1.2-1 crashes on start?"
date: 2005-11-22
forum: Desktop Environments
---

### Post by thumbsoup on 2005-11-22
Just downloaded the deb file for BUM, linked from the developer's page to a  Debian package site.   

Installed it:

sudo dpkg -i bum_2.1.2-1_all.deb

I can now see BootUp-Manager icon in System-->Administration, but when I click on it, it seems to start to open, with a minimized window, but then that dissappears.   When I tried to open it again, I get this error message in a small window:

"Another bum is running, or  the file: /var/lock/bum remains locked!"

Don't see bum in System Monitor.

How do I get BootUp-Manager to run?

Thanks.

---

### Post by gabhla on 2005-11-22
ditto....very same problem.

---

### Post by thumbsoup on 2005-11-22
Anyone have a working install of version 2.1.2-1 ?

Or are you using 2.1.1 ?

Thanks.

---

### Post by saltydog on 2005-11-27
[QUOTE=thumbsoup]Just downloaded the deb file for BUM, linked from the developer's page to a  Debian package site.   

Installed it:

sudo dpkg -i bum_2.1.2-1_all.deb

I can now see BootUp-Manager icon in System-->Administration, but when I click on it, it seems to start to open, with a minimized window, but then that dissappears.   When I tried to open it again, I get this error message in a small window:

"Another bum is running, or  the file: /var/lock/bum remains locked!"

Don't see bum in System Monitor.

How do I get BootUp-Manager to run?

Thanks.[/QUOTE]


sudo rm -rf /var/lock/bum

sudo bum

---

### Post by gabhla on 2005-11-27
Hello.  Did it, and here'w what I got :

steven@ubuntu:~$ sudo rm -rf /var/lock/bum
Password:
steven@ubuntu:~$ sudo bum
sudo: bum: command not found
steven@ubuntu:~$
 
Now the icon is gone.

---

### Post by tomski on 2005-12-06
i dont get no error message it asks me for root pwd then my system just locks up (maybe x is crashing?)

---

### Post by magnusbb on 2005-12-06
I use 2.1.3.-1, which seems to be the latest version. It can be found here, and it works.

[http://packages.debian.org/unstable/admin/bum](http://packages.debian.org/unstable/admin/bum)

---

