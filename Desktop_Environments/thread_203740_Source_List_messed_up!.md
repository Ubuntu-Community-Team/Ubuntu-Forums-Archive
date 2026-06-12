---
title: "Source List messed up!"
date: 2006-06-25
forum: Desktop Environments
---

### Post by Magiczero on 2006-06-25
I installed automatix on my 6.06 system and it said that it was going to overwrite my source list file and I told it no and it did it anyway!!!!  Can anyone give me their source.list because there is nothing in mine and that is not good!!!:(   Can I get some help here please!!!???  All I need is a source file!!  Thanks Alot

---

### Post by aysiu on 2006-06-25
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) should help you get a good sources.list

Incidentally, Automatix makes a backup copy of your old sources.list before overwriting it.

---

### Post by arnieboy on 2006-06-25
[QUOTE=Magiczero]I installed automatix on my 6.06 system and it said that it was going to overwrite my source list file and I told it no and it did it anyway!!!!  Can anyone give me their source.list because there is nothing in mine and that is not good!!!:(   Can I get some help here please!!!???  All I need is a source file!!  Thanks Alot[/QUOTE]
the default option on automatix restores your sources.list. You chose the other option. Next time READ more carefully.
By the way which version of automatix were you using?
386/amd64/ppc ?

The time and date based sources.list backup is in your /etc/apt folder

---

### Post by aysiu on 2006-06-25
[QUOTE=arnieboy]the default option on automatix restores your sources.list. You chose the other option. Next time READ more carefully.[/QUOTE]
Thanks for the clarification, arnieboy.

---

### Post by arnieboy on 2006-06-25
by the way if the package was the powerpc one then *the missing sources.list* had to do with an antiquated (and borked)  powerpc version whose maintainer is currently on vacation. We have released an updated version for the time being and that should take care of this error.

---

