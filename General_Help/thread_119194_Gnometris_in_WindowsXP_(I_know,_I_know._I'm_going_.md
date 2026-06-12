---
title: "Gnometris in WindowsXP? (I know, I know. I'm going to get guillotined.)"
date: 2006-01-18
forum: General Help
---

### Post by RoninGurl on 2006-01-18
I'm likely to get guillotined after being labeled a troll and then put on display in town square to make an example to remind those who have not been so bold yet. But I can't resist asking. As I do use Ubuntu. :-p So maybe that will save my life for the moment. Well enough with that. I'll get on topic now. 

Is there anyway to run Gnometris in Windows XP with the GTK plug-in that xchat and GAIM use to run successfully in Windows XP? I'd love to run Gnometris on Windows XP because I think it's literally one of the best remakes of Tetris I've encountered and actually closer to the original than many others I've found. Any help? Pretty please! With a cherry on top!!! Maybe even a strawberry daiquiri if that's your thing.

---

### Post by az on 2006-01-19
Cygwin in a unix environment for W32.  You should be able to install Cygwin and compile and run most software that runs on linux, since linux is a unix-type environment.

It even comes with X.

I am not up to speed as to wheter GTK2 is ported to cygwin.  I think so, but I am not sure.

---

### Post by az on 2006-01-19
Good luck:

[http://web.sfc.keio.ac.jp/~sakai/cygwin/index.html.en](http://web.sfc.keio.ac.jp/~sakai/cygwin/index.html.en)

[http://cygnome.sourceforge.net/](http://cygnome.sourceforge.net/)

---

### Post by RoninGurl on 2006-01-19
No, what I meant was running under Windows with the GTK+ runtime that GAIM and xchat make use of to run in Windows XP. Would Gnometris not run in similar conditions?

---

### Post by az on 2006-01-19
You would have to try it.  I guess that GTK2 port that Gaim and Xchat use is available to Cygwin.  If there is no precompiled version of an app, you can build it in windows with the cygwin toolchain.


I don't think there is a prebuilt W32 version of gnometris.

---

