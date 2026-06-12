---
title: "Installing old program with old libraries"
date: 2009-01-19
forum: General Help
---

### Post by Mr_H on 2009-01-19
I currently have a server running Ubuntu 8.10.  Works nice, love it.

I would like to use it to host a gaming server for an older game (Tribes 2).  Trying the installation the normal way with the program results in errors indicating that I'm using the wrong libraries.  Apparently Tribes2 isn't compatiable with our latest libraries.  Fortuantly some kind soul compiled old, compatiable libraries, but I'm having some issues with it.

I know that I somehow have to get the installer to use the old libraries instead of the newer ones.  From the documentation I read, it seems I have to do the following commands:

```

linux32 (It's not compatiable with 64 bit apparently)

export _POSIX2_VERSION=199209  (This is required because of some other error)
export COMPAT=home/t2server/Loki_Compat
export LD_PRELOAD=/$COMPAT/libstdc++-3-libc6.2-2-2.10.0.so:/$COMPAT/libSDL-1.2.so.0


```


Then I run the installer (./tribes2d-wincd.run) and receive the following error:

```

ERROR: ld.so: object '/home/t2server/Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so' from
 LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/home/t2server/Loki_Compat/libSDL-1.2.so.0' from LD_PRELOAD cann
ot be preloaded: ignored.
The setup program seems to have failed on x86/ERROR: ld.so: object '/home/t2server/Lok
i_Compat/libstdc++-3-libc6.2-2-2.10.0.so' from LD_PRELOAD cannot be preloaded: ignored
.
ERROR: ld.so: object '/home/t2server/Loki_Compat/libSDL-1.2.so.0' from LD_PRELOAD cann
ot be preloaded: ignored.
glibc-2.0

```

(This error repeats a couple of times as there's 2 or 3 different 'install' parts).

Am I doing the process wrong, missing something obvious?  I haven't worked with these commands before, so I'm still learning. Any suggestions would be greatly appreciated.  :)

H

---

### Post by compiledkernel on 2009-01-19
Your trying to use the old Loki build of Tribes2? 

I thought I was the only one that actually had one of those.

---

