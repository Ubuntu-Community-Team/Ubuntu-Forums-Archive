---
title: "Unable to compile glib latest version"
date: 2011-07-04
forum: Desktop Environments
---

### Post by ~!geek!~ on 2011-07-04
Hey, I am trying to build latest gtkmm on ubuntu 11.04 amd64 machine which requires glib as one of its dependency. But its causing error 


The error is :
> 
./.libs/libgobject-2.0.so: undefined reference to `g_cclosure_marshal_BOOLEAN__BOXED_BOXED'
./.libs/libgobject-2.0.so: undefined reference to `g_cclosure_marshal_VOID__PARAM'
./.libs/libgobject-2.0.so: undefined reference to `g_cclosure_marshal_BOOLEAN__FLAGS'
collect2: ld returned 1 exit status
make[4]: *** [gobject-query] Error 1
make[4]: Leaving directory `/home/test/glib/gobject'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/test/glib/gobject'
make[2]: *** [all] Error 2
The output of ./configure command is:
[http://pastebin.com/DSyQrF1c](http://pastebin.com/DSyQrF1c)

The output of make command with errors is:
[http://pastebin.com/bAgd3UiK](http://pastebin.com/bAgd3UiK)


Any Solutions!!!!

---

