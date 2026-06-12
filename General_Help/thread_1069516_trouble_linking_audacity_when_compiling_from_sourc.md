---
title: "trouble linking audacity when compiling from source"
date: 2009-02-14
forum: General Help
---

### Post by macho on 2009-02-14
hi there.  i had some unexpected crashes in the ubuntu garden variety audacity package, so i thought i'd install from source to see if i couldn't figure out what was going on and send a patch.  unfortunately i'm having trouble getting it compiled, when running 'make', at the linking stage i get:
```

/bin/bash ../libtool --mode=link gcc  -O20 -ffast-math -mno-ieee-fp -D_REENTRANT -fsigned-char  -DUSE_MEMORY_H   -o libvorbis.la -rpath /usr/local/lib -no-undefined -version-info 3:0:3 mdct.lo smallft.lo block.lo envelope.lo window.lo lsp.lo lpc.lo analysis.lo synthesis.lo psy.lo info.lo floor1.lo floor0.lo res0.lo mapping0.lo registry.lo codebook.lo sharedbook.lo lookup.lo bitrate.lo -L../../libogg/src -logg -lm -L../../libogg/src -logg
libtool: link: cannot find the library `'
make[5]: *** [libvorbis.la] Error 1
make[5]: Leaving directory `/home/macho/Desktop/black mask/audacity/lib-src/libvorbis/lib'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/macho/Desktop/black mask/audacity/lib-src/libvorbis/lib'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/macho/Desktop/black mask/audacity/lib-src/libvorbis'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/macho/Desktop/black mask/audacity/lib-src/libvorbis'
make[1]: *** [libvorbis/lib/.libs/libvorbisenc.a] Error 2
make[1]: Leaving directory `/home/macho/Desktop/black mask/audacity/lib-src'
make: *** [audacity] Error 2
```


how am i to know which library it's having trouble with?

---

### Post by macho on 2009-02-14
i seem to have fixed the problem by removing a space in one of the directory names further up the path.

---

