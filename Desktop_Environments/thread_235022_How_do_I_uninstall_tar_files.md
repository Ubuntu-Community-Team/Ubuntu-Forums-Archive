---
title: "How do I uninstall tar files"
date: 2006-08-12
forum: Desktop Environments
---

### Post by floyd27 on 2006-08-12
Hi guys and gals..

I have installed nvclock and now whould like to remove it completely from my system
It required 
./configure
make
make install

Now I whould like to remove it.
Can someone please help here. There is no instructions on how to do this in the read-me or and posts i have read so far.
Thanx for the help

---

### Post by Ramses de Norre on 2006-08-12
There is no real way to uninstall it other then searching which files are installed by make install and deleting them.. This is a bit of a problem with compiling from source.
In many cases there is a file included with the source with instructions for which files to remove but it seems not to be so in your case..

A way to prevent this problem in the future is installing checkinstall en using sudo checkinstall instead of sudo make install, this command will create a deb you can install and later on remove with synaptic or dpkg -r. 
Only issue is that checkinstall doesn't work with all apps, but it does with a lot.

---

### Post by chavo on 2006-08-12
Just go back into the source directory and run -> sudo make uninstall.

If you've deleted the original directory just untar it again - run ./configure - and then run -> sudo make unistall.

---

### Post by slakkie on 2006-08-12
> **Ramses de Norre said:**
> 
A way to prevent this problem in the future is installing checkinstall en using sudo checkinstall instead of sudo make install, this command will create a deb you can install and later on remove with synaptic or dpkg -r. 
Only issue is that checkinstall doesn't work with all apps, but it does with a lot.

This sounds pretty funky.

---

### Post by jchau on 2006-08-12
> **chavo said:**
> Just go back into the source directory and run -> sudo make uninstall.

If you've deleted the original directory just untar it again - run ./configure - and then run -> sudo make unistall.

If you didn't have to use sudo to run "make install", you probably won't need sudo to "make uninstall" either.

---

