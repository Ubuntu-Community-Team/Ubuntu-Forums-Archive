---
title: "Emulators."
date: 2006-07-14
forum: Gaming &amp; Leisure
---

### Post by Just4 on 2006-07-14
I'm looking for some Linux emulators, so far I have gFCEU and ZSnes, but I am looking for a Genesis and 32X emulator specifically, what are the good ones available?

---

### Post by irish rebel on 2006-07-14
for sega games use dgen available from repos  and xmess or xmame for mame games fceu for nes games and snes or zsnes for super nintendo

---

### Post by hanzomon4 on 2006-07-16
Gens from cvs. works great under xgl/compiz.
```
cvs -d:pserver:anonymous@gens.cvs.sourceforge.net:/cvsroot/gens login
```

```
 cvs -z3 -d:pserver:anonymous@gens.cvs.sourceforge.net:/cvsroot/gens co -P GensForLinux
```

```
cd GensForLinux
``` 

next ```
 export CC=/usr/bin/gcc-3.4 
```

then just ```
./configure
``````
make
``` ```
sudo make install
```

---

