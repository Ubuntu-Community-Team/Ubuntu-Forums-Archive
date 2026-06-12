---
title: "Has anyone gotten mupen64plus to work with hardy?"
date: 2008-10-02
forum: Gaming &amp; Leisure
---

### Post by badfish69 on 2008-10-02
Running hardy 64 bit. I'm getting closer but there's still 2 errors at the end when I $make all from the mupen64plus source files. I'm not sure if it's a dependency issue or what, but I'm installing binaries like it's going out of style, and I still repeatedly get

```

make[1]: *** [Tmem_nasm.o] Error 1

```
and
```

make: *** [plugins/glide64.so] Error 2

```

---

### Post by klikklak on 2008-10-02
I got the one from playdeb and did dpkg -i --force-all to override the fact that it wasn't amd64.

---

### Post by hessiess on 2008-10-02
32 bit build works, 64 bit one locks up.

---

### Post by badfish69 on 2008-10-02
> **klikklak said:**
> I got the one from playdeb and did dpkg -i --force-all to override the fact that it wasn't amd64.

i couldn't figure out how to get the one from playdeb so i got it from getdeb instead. dpkg -i --force-all. crashes ubuntu when i try to load a rom

---

### Post by klikklak on 2008-10-03
It's typoed in the list on the site, but it's in the repos.  just install the playdeb package for the repos and then search for mupen and it'll show up.  Dunno about the crashing, do other opengl programs crash your setup?

---

