---
title: "Hotei Jewels Relax - works fine but no sound"
date: 2010-11-02
forum: Gaming &amp; Leisure
---

### Post by Sealbhach on 2010-11-02
Hi,
I downloaded the tar.bz2 for Hotei Jewels:Relax from here:

[http://www.wegroup.org/games/puzzle-logic/hoteis-jewels-relax.html](http://www.wegroup.org/games/puzzle-logic/hoteis-jewels-relax.html)

and extracted it to my /home/Games folder. It works fine when I press the hj file, but there is no sound.

Anyone know how to get the sound working? I'm using Ubuntu 10.04 64-bit.  

.

---

### Post by WienerWuerstel on 2010-11-02
Go with a Terminal into the Folder of the Game and try:

```
aoss ./hj
```

or

```
padsp ./hj
```

---

### Post by Sealbhach on 2010-11-02
Thanks, but neither of those worked. 

I got an error message with the oss one:

```
$ aoss ./hj
ERROR: ld.so: object '/usr/lib/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
```

I have already install the ia32 libs, but maybe I need a symlink or something?

.

---

### Post by Perfect Storm on 2010-11-03
You'll better wait for Ubuntu to get incorporated ossp.

The problem you get is that games that use the ancient oss sound api, is that - if the game is made to write directly to the sound memory in oss. Then padsp workaround won't work.


Hopefully Ubuntu will get the ossp proxy up in the next Ubuntu release.

---

### Post by Scampanero on 2011-07-11
Had same sound issue.
Problem solved with the installation of the required libraries:

libsdl-image1.2 
libsdl-mixer1.2 
libsdl-mixer1.2-dev

Great game!!

---

