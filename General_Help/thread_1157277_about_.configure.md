---
title: "about ./configure"
date: 2009-05-12
forum: General Help
---

### Post by subjugater on 2009-05-12
I am struggling with the instruction for [COLOR="Red"]./configure[/COLOR] on this page:

[https://help.ubuntu.com/community/CompilingSoftware#configure](https://help.ubuntu.com/community/CompilingSoftware#configure)


I have two basic questions:

1. where can I download the [COLOR="Red"]configure[/COLOR]? It should be a script or a package?

2. is there any other webpage can give more details on [COLOR="Red"]./configure[/COLOR]?

Thanks.

---

### Post by LoneWolfJack on 2009-05-12
the configure script should be part of any source file package that you download. it's not a file that you download somewhere because it is specific to the project it was created for. that's my udnerstanding at least.

---

### Post by baseface on 2009-05-12
when you download some source to be compiled, you run ./configure which creates the makefile.
you dont download it. lol.

---

### Post by logos34 on 2009-05-12
configure is a script--you already have it.

make is a program executable, which you call as the second step in compiling.

Chances are **build-essential** pkg will have most of the tools you need to start compiling right away.

> sudo apt-get install build-essential

What are you trying to install?

---

### Post by subjugater on 2009-05-12
> **logos34 said:**
> configure is a script--you already have it.

make is a program executable, which you call as the second step in compiling.

Chances are **build-essential** pkg will have most of the tools you need to start compiling right away.



What are you trying to install?

Thank you all for your prompt responses. In fact, I am trying to use Matlab to compile a fortran code by using matlab command [COLOR="Red"]mex[/COLOR].

I failed to do so. 'coz matlab can only work with gcc-4.2.0 or older version. The default on my desktop is gcc-4.2.4. I have gcc-4.1.0 as well. But I just don't know how to change the default to gcc-4.1.0.

Please see my previous thread about this.

[http://ubuntuforums.org/showthread.php?t=1156188](http://ubuntuforums.org/showthread.php?t=1156188)

---

### Post by subjugater on 2009-05-12
bump

---

### Post by logos34 on 2009-05-12
looks like you're going to have to recompile Matlab with the correct gcc version--use the options mc4man suggested in the other thread.

Either that or maybe [FreeMat]("http://freemat.sourceforge.net/index.html") will have a version of mex that will work (deb [here]("http://www.getdeb.net/search.php?keywords=matlab"), but hardy only)

or maybe I misunderstand your problem

---

