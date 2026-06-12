---
title: "Vnc"
date: 2009-01-17
forum: General Help
---

### Post by lenswipe on 2009-01-17
Hi all

When i type "vncviewer" in terminal i get this message:

> vncviewer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory


Anyone know whats going on here?


-Lenswipe

---

### Post by HermanAB on 2009-01-17
Well, two C libraries are missing.  Try installing the development tools.

---

### Post by lenswipe on 2009-01-17
> **HermanAB said:**
> Well, two C libraries are missing.  Try installing the development tools.

ive searched for the libraries in synaptic and it says they are installed...



how do i install development tools?

---

### Post by aesis05401 on 2009-01-17
sudo apt-get install libstdc++2.10-glibc2.2

This is supposed to resolve it.

---

### Post by lenswipe on 2009-01-17
> **aesis05401 said:**
> sudo apt-get install libstdc++2.10-glibc2.2

This is supposed to resolve it.

Well if i run that terminal says:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++2.10-glibc2.2


---

### Post by spartan_87 on 2009-01-17
I had this same exact problem. Took me forever to find a solution but I found on a few forums saying that if you install the libstdc++2.10-glibc2.2 package it has those libraries in it. You can try to get it from apt-get, but I couldn't so I downloaded it from the debian site, [http://packages.debian.org/stable/libs/libstdc++2.10-glibc2.2](http://packages.debian.org/stable/libs/libstdc++2.10-glibc2.2)
Installed it and it worked.

---

### Post by aesis05401 on 2009-01-17
[_Ubuntu Link_]("http://packages.ubuntu.com/gutsy/i386/libstdc++2.10-glibc2.2/download")

Apparently this dropped from the standard apt repos in 8.04.  I didn't know this, sorry.

---

### Post by lenswipe on 2009-01-18
thanks ppl

i got it installed...


Now to see if VNC works :P


EDIT: YEEESS! TY guys!

-L

---

