---
title: "gtk+ 2.2.0"
date: 2009-02-02
forum: Desktop Environments
---

### Post by Typhoeus on 2009-02-02
I'm quite new to linux and enjoying the challenges.

My problem at the min is getting a BBC emulator to work with xubuntu 8.04. I've tried sdlmess with kxmame as a front end. The mame side works well but cant get to grips with the mess side of things, i've downloaded the bios files and there in the right folder, some emulators work BBC don't.

I next found beebem 0.0.13.  which had to be compiled from source. This turned out to be fun as trying to compile from source has always been fruitless. Anyways this time I've cracked it ( with help from [http://ubuntuforums.org/showthread.php?t=323939&highlight=compile+source+code](http://ubuntuforums.org/showthread.php?t=323939&highlight=compile+source+code) ) my only problem now is that I need gtk+2.2.0. Below is the relevant output from running...

                   ./configure --enable-econet
-
-
checking for GTK+ - version >= 2.2.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: mypkgname 0.1 needs GTK+ 2.2.0

I seems that gtk+2.2.0 is quite old but i cant find it anywere.

Please help either with an xubuntu bbc emulator of gtk+ 2.2.0

nice one folks

---

### Post by snova on 2009-02-02
Install **libgtk2.0-dev**.

---

### Post by Typhoeus on 2009-02-03
Its so easy when you know how. 

Thanks my friend

---

