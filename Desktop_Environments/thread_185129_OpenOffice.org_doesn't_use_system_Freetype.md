---
title: "OpenOffice.org doesn't use system Freetype?"
date: 2006-05-31
forum: Desktop Environments
---

### Post by e_liming on 2006-05-31
Hi all,
I use Xubuntu with latest updates. I notice that the openoffice.org packages doesn't have BCI enabled whereas the system font does. 

Can anyone confirm this and btw, can I symlink the system freetype to openoffice? I did this without any results.

TIA

---

### Post by e_liming on 2006-05-31
So Ubuntu has no problem of this? Is it a specific Xubuntu problem?

---

### Post by nalthien on 2006-05-31
It is my understanding that Openoffice uses a statically linked version of freetype for its font rendering; so it definitely does not use the system version.  Since the library is compiled into the program itself, I don't think there is a way to load a different version of that library.

---

### Post by e_liming on 2006-05-31
Just curious why the ubuntu team made this decision? If they worry about the BCI patent they should have not enable BCI in the system freetype library.

I guess this is about stability concern?

---

### Post by tardis_junkie on 2006-05-31
It is the open office team who made this decision - annoying as it is, why they couldn't just leave it to use the system freetype library.

---

### Post by e_liming on 2006-05-31
I think the Ubuntu team should be able to enable the BCI in the freetype that comes with OpenOffice when they build the OpenOffice package, just un-comment out 1 line of code then that's it.

---

### Post by rubengs on 2006-09-01
It's posible to disable the bytecode and make openoffice to use the autohinter, just recompile the freetype package with these simple instructions: 

[http://ubuntuforums.org/showthread.php?t=84359&highlight=openoffice](http://ubuntuforums.org/showthread.php?t=84359&highlight=openoffice)

Change version numbers to match dapper package an thats all.

---

