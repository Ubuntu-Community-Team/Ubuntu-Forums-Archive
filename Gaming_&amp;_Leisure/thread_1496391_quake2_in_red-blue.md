---
title: "quake2 in red-blue"
date: 2010-05-29
forum: Gaming &amp; Leisure
---

### Post by Kyh31 on 2010-05-29
I found this website: [http://www.jfedor.org/red-blue-quake2/](http://www.jfedor.org/red-blue-quake2/)
It describes how you could compile quake2 so you can use red-blue-glasses to play quake2 in 3D.

I tried it but i get following errors:

mkdir: cannot create directory `debugi386-glibc': File exists
mkdir: cannot create directory `debugi386-glibc/client': File exists
mkdir: cannot create directory `debugi386-glibc/ded': File exists
mkdir: cannot create directory `debugi386-glibc/ref_soft': File exists
mkdir: cannot create directory `debugi386-glibc/ref_gl': File exists
mkdir: cannot create directory `debugi386-glibc/game': File exists
mkdir: cannot create directory `debugi386-glibc/ctf': File exists
make: [build_debug] Error 1 (ignored)
make targets BUILDDIR=debugi386-glibc CFLAGS="-Dstricmp=strcasecmp -g"
make[1]: Entering directory `/home/koen/Downloads/quake2-3.21/linux'
gcc -Dstricmp=strcasecmp -g -fPIC -o debugi386-glibc/game/g_items.o -c ../game/g_items.c
../game/g_items.c:43: error: static declaration of ‘jacket_armor_index’ follows non-static declaration
../game/g_local.h:461: note: previous declaration of ‘jacket_armor_index’ was here
../game/g_items.c:44: error: static declaration of ‘combat_armor_index’ follows non-static declaration
../game/g_local.h:462: note: previous declaration of ‘combat_armor_index’ was here
../game/g_items.c:45: error: static declaration of ‘body_armor_index’ follows non-static declaration
../game/g_local.h:463: note: previous declaration of ‘body_armor_index’ was here
make[1]: *** [debugi386-glibc/game/g_items.o] Error 1
make[1]: Leaving directory `/home/koen/Downloads/quake2-3.21/linux'
make: *** [build_debug] Error 2


Is this someone who can help me out installing this?

greetz,
Koen

---

