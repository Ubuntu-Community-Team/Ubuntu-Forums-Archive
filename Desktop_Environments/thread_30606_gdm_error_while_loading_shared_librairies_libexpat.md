---
title: "gdm: error while loading shared librairies libexpat.so.1"
date: 2005-04-29
forum: Desktop Environments
---

### Post by sissou on 2005-04-29
Hello everybody,
I can't log in Ubuntu Hoary with gnome  [-X , here's the error message :

[INDENT]gdm: error while loading shared librairies libexpat.so.1
Cannot open shared object file : Input/Output error[/INDENT]

I'm a new linux user and really don't know how to fix this problem.  ](*,) 

Thanks for your help

---

### Post by alastair on 2005-04-29
Maybe some help. The package is "libexpat1" and has files :

/usr/lib/libexpat.so.1.0.0
/usr/share/doc/libexpat1
/usr/share/doc/libexpat1/copyright
/usr/share/doc/libexpat1/changelog.gz
/usr/share/doc/libexpat1/changelog.Debian.gz
/usr/lib/libexpat.so.1
/usr/lib/libexpat.so.0

So I would check that those files exist i.e.

ls -l /usr/lib/libexpat.so.1
file /usr/lib/libexpat.so.1

i.e. log in on a console (CTRL+ALT+F1) and check the above.

Perhaps reinstalling them would help e.g.

sudo apt-get --reinstall libexpat1

---

### Post by sissou on 2005-04-30
ls -l /usr/lib/libexpat.so.1
[INDENT]Returns me there's not file or folder libexpat.so.1[/INDENT]

sudo apt-get --reinstall libexpat1
Does not work  ](*,)

---

### Post by jobezone on 2005-04-30
The right command is:

sudo apt-get install --reinstall libexpat1

---

