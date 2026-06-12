---
title: "Source Code Doubts"
date: 2008-12-04
forum: Desktop Environments
---

### Post by sharathpaps on 2008-12-04
hi,
      I have no programming experience...but from all the reading i've been doing, I have realised that learning to compile source codes is one of the ways to understand & use linux effectively.. What I need to know is.. Is Source Code independent of platform? Can I use the same source code but different compilers to run a program in different platforms?

Could you please guide me on how to compile source code in Ubuntu 8.10..

Also please point to where I can learn the basics of Linuc...

{I am a NOOB}

---

### Post by cmay on 2008-12-04
you do not have to learn to compile from source to use linux. but it can be helpfull to know. the first thing is to download the build-essential package which has a compiler in it. then you find some program and read the instructions. it is almost always something with havinf some libraires you need to install first and then run in the terminal 
./configure  
make
make install 
and thats it. 

you can write source code that works on most computers and platforms and you cna write sources that only works for one type of computer and platform. the two examples are microssoft windows and xandros linux.  xandros has changed some things in the libraries that makes it not compatible with its father debian. 

hope it helped a little.
good luck.

---

### Post by sharathpaps on 2008-12-04
@cmay

Thanx a lot for responding so fast.. I'll try what you said...A lot of experience is the key...

---

### Post by cmay on 2008-12-04
good luck. :)

---

### Post by snova on 2008-12-04
Agreed with cmay, you don't need to know how most of the time. There are occasional reasons to (not in the repos, want a newer version, etc), though.

As to whether code can be compiled on different platforms... it depends on the code itself. If it uses features specific to one OS, it's either not possible or difficult. But if it only uses portable features, or has been ported to a variety of platforms already, it should be fine.

The "How" is usually explained in a file included with the source code, typically in a file named INSTALL.

---

