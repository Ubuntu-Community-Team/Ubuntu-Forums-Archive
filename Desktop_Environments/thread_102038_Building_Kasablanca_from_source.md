---
title: "Building Kasablanca from source"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Sajjen on 2005-12-11
I'm trying to build Kasablanca ( [http://kasablanca.berlios.de/](http://kasablanca.berlios.de/) ) from source. The ./configure step dies with the following message:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

What pagackes do I need to install?

Thanks
Erik

---

### Post by PMO6022 on 2005-12-11
I would guess you need at least libx11-dev.  

One tool you can use to figure out what extra packages you need to install to compile a program is apt-file. You can install it with a simple ```
sudo apt-get install apt-file
``` See [http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-cache]("http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-cache") and scroll down to section 5.4 "How to discover to which package a file belongs" for instructions on how to use it. 

Good luck

---

### Post by ERam123 on 2005-12-11
Why not just use konqueror as a ftp client?

---

### Post by coaxx on 2006-01-06
[QUOTE=ERam123]Why not just use konqueror as a ftp client?[/QUOTE]
does it support SSL and SFTP (SSH)?

---

### Post by Didier69 on 2006-01-06
Hi Sajjen,

[QUOTE=Sajjen]I'm trying to build Kasablanca ( [http://kasablanca.berlios.de/](http://kasablanca.berlios.de/) ) from source.[/QUOTE]

Did you succeded with compilation/installation of kasablanca ?

Regards.

---

### Post by coaxx on 2006-01-06
I did it today with dapper and it worked fine. I missed the Kmenue item though... AND the sftp feature. For that I am using Konqueror now: just use something like "sftp://root@192.168.1.1:222/etc/" in address bar or Bookmark

---

### Post by veloct on 2006-01-06
I have built it for breezy. You can download it at:

[www.veloct.net/files/kasablanca-0.4.0.2-1_i386.deb](www.veloct.net/files/kasablanca-0.4.0.2-1_i386.deb)

---

