---
title: "4 hours stuck with a little problem"
date: 2005-11-02
forum: Desktop Environments
---

### Post by mxyzptlk on 2005-11-02
how can i install a program unpacked from a tar.gz file i'm like to upgrade samba

any ideas please

my hand is hurting of being surfing wen pages of topics like this but nothing

10x in advanced


mxyzptlk

---

### Post by ltmon on 2005-11-02
Usually a tar.gz file is source code, which needs to be compiled.  It's a good idea not to do this, unless you know what you are doing and the program you need is not available in a standard repository (i.e. in Synaptic). 

Anyways... if you still want to give it a go:

> sudo apt-get install build-essential
> sudo apt-get install checkinstall

This will install all the software needed to actually compile a program

Given you have already said you need to install a new version of Samba, I suggest you also do

> sudo apt-get build-deps samba

Which will install a whole lot of stuff you need to compile Samba.

> tar xvfz <yourfile>.tar.gz

This will extract the source code from the tar.gz file (which is like a zip file)

> cd <yourfile>/

Move into the directory

> ./configure
> make
> sudo checkinstall -D make install

This does the actual compilation.  It will take a while.

The configure step may tell you that there are dependencies missing, in which case you need to find them.  Hopefully this won't be the case.

L.

---

### Post by thekurst on 2006-01-21
I tried to upgrade my samba doing the same thing, but my Ubuntu is still seems to be using the older version. Is it that the default install locations are different? and if so how do I point my system to use the new version I just installed?

Either way my install is still using the old version

---

