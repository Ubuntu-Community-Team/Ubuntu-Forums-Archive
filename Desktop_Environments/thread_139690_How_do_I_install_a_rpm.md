---
title: "How do I install a rpm"
date: 2006-03-04
forum: Desktop Environments
---

### Post by tidy_boy on 2006-03-04
hey guys I have downloeded some software Chandler_linux_0.6.1.i386.rpm 

How do I install it?


Thanks

---

### Post by bluevoodoo1 on 2006-03-04
[https://wiki.ubuntu.com/rpm?highlight=%28rpm%29](https://wiki.ubuntu.com/rpm?highlight=%28rpm%29)

---

### Post by taurus on 2006-03-04
You can use alien to convert it to .deb and install it with "dpkg -i" command.  Type "man alien" at the prompt for more details...

---

### Post by tidy_boy on 2006-03-04
awesome thanks a lot mate :D

---

### Post by tidy_boy on 2006-03-04
I have installed this but cant find where to open it [http://chandler.osafoundation.org/](http://chandler.osafoundation.org/)

I have tried in a terminal Chandler but does not work?

---

### Post by bluevoodoo1 on 2006-03-04
Hmmm, you could try "chandler" It might be case sensitive. Or "locate chandler" from a terminal ,or open up GNOME search and type chandler.  Look for something in /usr/bin/ that relates to chandler.

---

### Post by tidy_boy on 2006-03-04
Yeah Itried chandler and Chandler and locate chandler and serach and it did not find anything

---

### Post by ComplexNumber on 2006-03-04
[quote=tidy_boy]hey guys I have downloeded some software Chandler_linux_0.6.1.i386.rpm 

How do I install it?


Thanks[/quote] 
you can also use checkinstall (i think) to convert to debian.

---

### Post by bluevoodoo1 on 2006-03-04
[This page]("http://wiki.osafoundation.org/bin/view/Projects/BuildingChandler") says to try...     ./chandler or ./chandlerDebug

---

### Post by lisa on 2006-03-11
Try this:
> which chandler
and 
> /usr/local/chandler/chandler

I hope this will work.

See also (in german):

[http://forum.ubuntuusers.de/topic/23997/?highlight=chandler]("http://forum.ubuntuusers.de/topic/23997/?highlight=chandler")

---

### Post by %hMa@?b&lt;C on 2006-03-11
what does "chandler" Have to do with .rpms, that loads .PIM 
to install the rpm simplydo
```
 sudo apt-get install alien
```
then
[/code]sudo alien -di NAMEOFPACKAGE.RPM[/code]

---

### Post by bluevoodoo1 on 2006-03-11
[QUOTE=jeffc313]what does "chandler" Have to do with .rpms[/QUOTE]

Because... after it was installed, it could not be found... 

[QUOTE=tidy_boy]I have installed this but cant find where to open it [http://chandler.osafoundation.org/](http://chandler.osafoundation.org/)

I have tried in a terminal Chandler but does not work?[/QUOTE]

---

