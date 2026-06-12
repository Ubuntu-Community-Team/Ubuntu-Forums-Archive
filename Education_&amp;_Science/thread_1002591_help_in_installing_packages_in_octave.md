---
title: "help in installing packages in octave"
date: 2008-12-05
forum: Education &amp; Science
---

### Post by sadclownsmiles on 2008-12-05
hello.

i have installed GNU Octave version 3.0.1, and i've tried installing packages (sound/audio, and image) using: 

pkg install audio-1.1.2.tar.gz

but i got these as error messages:

configure: WARNING: no mkoctfile found on path./configure: line 2790: conftest.cc: command not found
configure: error: Could not run
error: the configure script returned the following error:
c
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables
checking for suffix of object files... o
checking for whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accetp ISO C89... none needed 
checking for mkoctfile... no
error: called from 'pkg:configure_make' in file /usr/share/g.m near line 1232, column 2

i got the file from [http://octave.sourceforge.net/packages.html](http://octave.sourceforge.net/packages.html)

i was wondering if there is another way that i could install basically sound.m, imread.m and imshow.m in octave. thank you.:D

---

### Post by jpkotta on 2008-12-08
In Intrepid, all of the octave-forge packages are in the repos again.
```
sudo aptitude install octave-audio
```
If you want to build them yourself, you need to install octave3.0-headers and build-essential.

---

