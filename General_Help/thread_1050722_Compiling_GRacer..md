---
title: "Compiling GRacer."
date: 2009-01-25
forum: General Help
---

### Post by Racecar56 on 2009-01-25
Ok, I want to compile [GRacer]("http://www.gracer.sf.net"), how do I get it compiled? It wants tcl 8.0 but I want to keep tcl 8.4 because of my aMSN. What to do, run a ancient (approximately from 1999-2000) Linux distro in VirtualBox? Thanks! [COLOR="White"][SIZE="1"]i hope i put it in the right category[/SIZE][/COLOR]
EDIT: Fixed typo.

[COLOR="Red"]SOLVED[/COLOR]

---

### Post by Racecar56 on 2009-01-30
Bump.
(Happy almost February :popcorn:)

---

### Post by Racecar56 on 2009-02-02
Good news.
I got GRacer working on a virtual machine with FreeBSD 7.1. :D
Easy, if you wanted to do this on your freebsd vm as root(yes I know this is ubuntu forum, not freebsd):

```
cd /usr/ports/games/gracer
make
make install
```
To launch GRacer you'd obviously type this command:
```
gracer
```
It works, it might need 3D acceleration though.

---

