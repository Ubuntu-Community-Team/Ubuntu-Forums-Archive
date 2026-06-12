---
title: "&quot;checkinstall&quot; not working"
date: 2005-10-14
forum: Desktop Environments
---

### Post by LinkRJH on 2005-10-14
linkrjh@ubuntu:~$ sudo apt-get install checkinstall
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package checkinstall
linkrjh@ubuntu:~$

---

### Post by Ampersand on 2005-10-14
It's in the Universe repository. 

Run 
```
sudo gedit /etc/apt/sources.conf
``` 
and remove the # at the start of all the lines beginning with 'deb' (it gives instructions in the file). Then run 'sudo apt-get update and try again.

---

### Post by LinkRJH on 2005-10-14
...my sources.conf is an empty file...do I need to fill it with something?

Richard

---

### Post by Ampersand on 2005-10-14
Try doing it this way:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto).

The method is the same for Breezy as Hoary.

---

