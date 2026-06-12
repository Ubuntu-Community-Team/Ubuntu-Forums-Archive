---
title: "Ubuntu 8.10 and ioquake3 1.34 error"
date: 2008-11-09
forum: Gaming &amp; Leisure
---

### Post by _algol_ on 2008-11-09
I can't be the first to have this problem, but I'm not seeing any other posts on it.

I upgraded from 8.04 to 8.10 this afternoon, and in the process of doing so apparently broke my ioquake3 installation.  

Running from the terminal gives the error at bottom.  It looked like a dependency issue to me, so I reinstalled the "libopenal1" package in Synaptic (ver. 1:1.3.253-4ubuntu1), but no dice.

Any ideas? 

mh@VIKING-1:~/games/ioquake3$ sh ioquake3
./ioquake3.i386: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory

---

### Post by _najt on 2008-11-11
Hi,
got the same problem but fortunately it's already solved here thanks to user gladstone:
[http://ubuntuforums.org/showthread.php?p=6140634](http://ubuntuforums.org/showthread.php?p=6140634)

If you're a beginner to Ubuntu (like me) it might need a little explanation.

The shared library is now (in Interpid) libopenal1 instead of libopenal0.

To fix it do what follows:
1) Open the terminal. I think you need administrative rights so just switch to root:
```
$ su root
```
2) Now navigate to usr/lib directory.
```
#cd usr/lib
```
3) What you have to do is to create a link to the proper shared library and name it libopenal.so.0. To do so write either of these two:
```
#ln -s libopenal.so.1.3.253 libopenal.so.0 
```
(this creates a direct link to the shared library)
```
#ln -s libopenal.so.1 libopenal.so.0
```
(this creates a link to the link that links to the library ;)
4) Enjoy iquake3...

---

### Post by _algol_ on 2008-11-12
Rock on!  Worked like a charm, thank you.  :guitar:

---

### Post by _najt on 2008-11-15
Glad it worked :)

---

