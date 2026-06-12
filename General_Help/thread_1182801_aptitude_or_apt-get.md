---
title: "aptitude or apt-get"
date: 2009-06-09
forum: General Help
---

### Post by A_M_S on 2009-06-09
hi.

Is there any advantage in apt-get over aptitude?


The aptitude saves the packages dependencies which can save a lot of work when uninstalling some aplications (kde for example).



Thanks

---

### Post by Soul-Sing on 2009-06-09
DESCRIPTION
       apt-get is the command-line tool for handling packages, and may be
       considered the user´s "back-end" to other tools using the APT library.
       Several "front-end" interfaces exist, such as dselect, aptitude,
       synaptic, gnome-apt and wajig.

There are not many diff. between apt-get and aptitude. Aptitude is a frontend for apt-get. Some people claim aptitude makes another more complete database, which is in my opinion not longer the case.
apt-get will do.

---

### Post by raymondh on 2009-06-09
> **leoquant said:**
>  
apt-get will do.

+1

---

### Post by A_M_S on 2009-06-09
tnx!

---

### Post by kevdog on 2009-06-09
I like aptitude myself, but who asked me?

---

### Post by boban on 2009-06-09
aptitude: better dependency handling, search feature etc.

Googling a bit reveals many useful comments about this topic, e.g., [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by Zorael on 2009-06-09
I also prefer aptitude. I'd like to say it really shines if/when you're trying out downloaded packages or external ppas, or when you just generally run into dependency errors.

apt-get will detect them, complain and prompty exit. aptitude will offer solutions.

It does run a bit slower, though. Nowadays when you can use apt-get autoremove, they're fairly equal.

---

