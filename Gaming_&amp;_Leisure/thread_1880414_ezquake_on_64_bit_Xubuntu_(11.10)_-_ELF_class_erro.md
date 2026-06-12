---
title: "ezquake on 64 bit Xubuntu (11.10) - ELF class error"
date: 2011-11-13
forum: Gaming &amp; Leisure
---

### Post by lorin30 on 2011-11-13
Haven't had much luck searching around for info on this error when trying to run nquake/ezquake:

./ezquake-gl.glx: error while loading shared libraries: libXxf86dga.so.1: wrong ELF class: ELFCLASS64
 
From what I gather it's something to do with a missing lib32 package(?) which is honestly beyond my understanding.  Is this something I can download/install somehow or am I better off trying to get WINE running? (though I'd prefer not to.)

---

### Post by thatguruguy on 2011-11-13
You should consider downloading the correct version of the game for your platform.

You can download the 64-bit version of ezquake from [here]("http://ezquake.sourceforge.net/").

---

### Post by lorin30 on 2011-11-13
Thanks for the tip.  ezquake was installed as part of nquake automatically so that didn't occur to me.

---

### Post by Perfect Storm on 2011-11-14
> ./ezquake-gl.glx: error while loading shared libraries: libXxf86dga.so.1: wrong ELF class: ELFCLASS64


Install libxxf86dga1:i386

---

