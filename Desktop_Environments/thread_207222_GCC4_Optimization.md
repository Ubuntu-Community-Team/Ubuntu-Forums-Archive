---
title: "GCC4 Optimization"
date: 2006-07-01
forum: Desktop Environments
---

### Post by Don_DiZzLe on 2006-07-01
Hello everyone,

I've been experimenting with some optimization flags and this is what I got so far:

"-march=athlon64 -02 -pipe -fprofile-generate -fforce-addr -ftree-loop-linear -ftree-loop-im -funswitch-loops -funroll-loops -floop-optimize2 -fprefetch-loop-arrays -ffast-math" 

and then I recompile with the following options:

"-march=athlon64 -02 -pipe -fprofile-use -fforce-addr -ftree-loop-linear -ftree-loop-im -funswitch-loops -floop-optimize2 -fprefetch-loop-arrays -ffast-math"

If someone has better suggestions please let me know, also let me know what u think about my flags.

---

### Post by Don_DiZzLe on 2006-07-02
Anyone?

---

### Post by jchau on 2006-07-02
Well, if you really need more speed, and you don't care about data storage space usage, you can try the option "-O3".

---

### Post by Don_DiZzLe on 2006-07-02
Yup, already did that. Anything else?

---

### Post by thasheep on 2006-07-02
What are you trying to recompile? Some packages respond well and others really poorly (break or run slower) with aggressive optimisations. Another thing you could look into is LDFLAGS

Another thing, you should have a look at what the "experts" of aggressive compilation optimisations have to say. Have a look at [http://forums.gentoo.org](http://forums.gentoo.org). [Gentoo](www.gentoo.org) is a source based distro.

---

### Post by Don_DiZzLe on 2006-07-02
What Im tryin to compile is this [http://hard-light.net/wiki/index.php/Fs2_open_on_Linux](http://hard-light.net/wiki/index.php/Fs2_open_on_Linux), an executable for the game Freespace2

---

### Post by thasheep on 2006-07-02
-ftree-vectorize works well for a lot of things.

---

