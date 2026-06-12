---
title: "Having Trouble Installing X-Plane."
date: 2009-12-20
forum: Gaming &amp; Leisure
---

### Post by kplt91 on 2009-12-20
I have tried with every Ubuntu version but I am having no luck on any, here is a copy of my terminal, can you help?

name@name-desktop:~$ sudo ln –s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
[sudo] password for name: 
ln: target `/usr/lib/libopenal.so.0' is not a directory
name@name-desktop:~$ cd Desktop
name@name-desktop:~/Desktop$ ./”X-Plane DVD Installer Linux”
bash: ./”X-Plane: No such file or directory
name@name-desktop:~/Desktop$ 

That was supposed to bring up the installer and everything and I am sure I have everything in place.

---

### Post by opensourcederry on 2009-12-26
Try this for Ubuntu 9.10, may give you some pointers.

[http://www.ilovelinux.co.uk/xplane910-1.php](http://www.ilovelinux.co.uk/xplane910-1.php)

---

### Post by Perfect Storm on 2009-12-26
If you're using 64-bit version of Ubuntu, you need to symblink the libopenal libs in the /usr/lib32

---

