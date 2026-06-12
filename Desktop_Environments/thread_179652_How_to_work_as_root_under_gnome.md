---
title: "How to work as root under gnome"
date: 2006-05-20
forum: Desktop Environments
---

### Post by moshenahon on 2006-05-20
I need to reinstall apache2.
after reinstallation, the etc/apache2 files remain the same and are not reset.
I want to delete them in order to reinstall apache2, but in order to delete the directory I need
to become root.
is there a convenient way to do so??

---

### Post by bluevoodoo1 on 2006-05-20
This might help...
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by S{yndrom}e on 2006-05-20
easy.

sudo rm /etc/apache2

---

### Post by Ramses de Norre on 2006-05-20
Use ```
sudo rm **-rf** /etc/apache2
``` if you don't want questions whether your sure or complaints about the directory not being empty.

---

### Post by bluevoodoo1 on 2006-05-20
[QUOTE=S{yndrom}e]easy.

sudo rm /etc/apache2[/QUOTE]

Might need to use the remove directory command instead.

[http://en.wikipedia.org/wiki/Rmdir](http://en.wikipedia.org/wiki/Rmdir)

---

### Post by S{yndrom}e on 2006-05-20
[QUOTE=bluevoodoo1]Might need to use the remove directory command instead.

[http://en.wikipedia.org/wiki/Rmdir](http://en.wikipedia.org/wiki/Rmdir)[/QUOTE]
my bad =P

---

### Post by Ramses de Norre on 2006-05-20
rmdir only works on empty directories, so you'll need to empty the directory first. Using rm with the -r option removes the directory with all of it's contents.

---

### Post by bluevoodoo1 on 2006-05-20
[QUOTE=Ramses de Norre]rmdir only works on empty directories, so you'll need to empty the directory first. Using rm with the -r option removes the directory with all of it's contents.[/QUOTE]

what about rmdir -rf /blah/blah  ??

(technically it's the same as rm -r... right? [with 4 fewer letters])

---

### Post by Ramses de Norre on 2006-05-20
rmdir doesn't support these options.. only possibilty is rmdir -p /folder1/folder2/folder3  which will delete folder3 first, then folder2 and then folder1, but still folder3 needs to be empty. And you'll need to be carefull with defining the path (you'll need to cd to the directory one level above folder1).

---

### Post by bluevoodoo1 on 2006-05-20
[QUOTE=Ramses de Norre]rmdir doesn't support these options.. only possibilty is rmdir -p /folder1/folder2/folder3  which will delete folder3 first, then folder2 and then folder1, but still folder3 needs to be empty. And you'll need to be carefull with defining the path (you'll need to cd to the directory one level above folder1).[/QUOTE]


Ohhhhhh, OK. I got you know!

---

