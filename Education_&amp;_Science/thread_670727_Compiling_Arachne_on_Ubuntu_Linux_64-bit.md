---
title: "Compiling Arachne on Ubuntu Linux 64-bit"
date: 2008-01-17
forum: Education &amp; Science
---

### Post by RSBhan on 2008-01-17
Is anyone familiar with compiling the Arachne genome assembly program on Ubuntu?  I am getting an error during the compiling process that reads as follows:

```
make: *** No rule to make target 'cvs/Cvs.h', needed by 'util/Ls.o'.  Stop.
```

There is a 'Cvs.h' file in a 'CVS' directory (not 'cvs').  Is this the source of the problem?  Any advice would be appreciated.  Thanks.

---

### Post by thisismalhotra on 2008-01-17
Is there a configure script in there ... if yes ... you might need to run that first to make rules for 'make'

do following steps

./configure
sudo make

Lot of people do make install here but if it is better to install a package checkinstall from synaptic and then do

sudo checkinstall

this install in a package manager way and will give you a .deb in the end which comes in handy for re installation plus you can give it to your frens using ubuntu and then they  do nt need to compile it from source. Also, checkinstall help when you r trying to uninstall as it deos a better dependency removal.

this might help you !!

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

if still doesnot work let us know

---

### Post by RSBhan on 2008-01-18
Thanks for the response.

There is no configure script in the directory.  A makefile already exists and the installation seemed to be proceeding well until about halfway through when I got the previous error message.

I did install the checkinstall package and when I run it I get this error message:

```
make: *** No rule to make target 'install'.  Stop.
```

Any other ideas?

---

### Post by RSBhan on 2008-01-23
I'm hoping someone can still offer some assistance with my problem of compiling the Arachne genome assembly program on our 64-bit Ubuntu machine.  Thanks in advance.

---

