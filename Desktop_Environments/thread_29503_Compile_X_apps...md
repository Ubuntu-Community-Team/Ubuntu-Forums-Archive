---
title: "Compile X apps.."
date: 2005-04-24
forum: Desktop Environments
---

### Post by Sonic-NKT on 2005-04-24
hi,
tried to compile pearpc.. so i first installed GCC and now i need x development files..
in the past i just used the xfree86-devel package, but since ubuntu uses x.org what should i install now?
searched for a ubuntu xorg devel package but cant find one.
can someone help me?
thanks
bye

EDIT:
or am i doing something wrong?
searched with google for a dev package and found one, but i think it would be better to use a ubuntu package. or is something else missing..
i get this error:

checking for X... no
checking for XOpenDisplay in -lX11... no
configure: error: Could not find XOpenDisplay in -lX11.

thats it.. before i got some compile errors but after installing gcc 3.3 they were gon e

---

### Post by alastair on 2005-04-24
There are quite a few X dev packages - but this might grab a few :

apt-get install x-dev

---

