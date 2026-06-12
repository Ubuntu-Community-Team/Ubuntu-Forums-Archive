---
title: "fuse too fast with sound"
date: 2010-10-28
forum: Gaming &amp; Leisure
---

### Post by j002 on 2010-10-28
I have an AMD 2400+ embedded soundcard, 256Mb running karmic (9-10).

I have got Fuse, Sinclair Spectrum emulator, installed from .deb files (SDL and GTK+), and complied from source.

They all do the same thing ; when it runs at 100% it runs too fast.

If I turn off the sound it runs fine.
If I run it at another speed it runs fine but no sound.

What gives ?

Is there any way I can change the sound-wossname (alsa, esd, etc) it uses ?

---

### Post by vldo on 2010-10-31
I have similar problem with fuse and sound. Without sound everything is ok. But with sound it is jerky.

I also tried to run it with ```
padsp fuse
``` but iwith no effect.

Im running ubuntu 10.10 x64

Does anybody have similar problem?

---

### Post by afrodeity on 2011-02-06
try man fuse, there are some options like

```

fuse --sound-device alsa

```

I have same problem, still trying to figure out the best setting. Will let you know if I solve the probelm

---

### Post by afrodeity on 2011-02-06
You can also try the oss wrapper:

```

aoss fuse

```

---

