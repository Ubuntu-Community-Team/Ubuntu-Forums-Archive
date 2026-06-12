---
title: "how to install alienarena7_32 version"
date: 2009-12-05
forum: Gaming &amp; Leisure
---

### Post by yasasflash on 2009-12-05
hey guys, i get the following error when i try to install Alien Arena 2009
i changed directory to the source directory and invoked the make command.
and this output is shown in the console.

```

client/snd_file.c:30:31: error: vorbis/vorbisfile.h: No such file or directory
client/snd_file.c:223: error: expected declaration specifiers or ‘...’ before ‘ogg_int64_t’
client/snd_file.c: In function ‘ovbfr_seek’:
client/snd_file.c:232: error: ‘offset’ undeclared (first use in this function)
client/snd_file.c:232: error: (Each undeclared identifier is reported only once
client/snd_file.c:232: error: for each function it appears in.)
client/snd_file.c: At top level:
client/snd_file.c:265: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ovbfr_callbacks’
client/snd_file.c: In function ‘ReadVorbisFile’:
client/snd_file.c:276: error: ‘ogg_int64_t’ undeclared (first use in this function)
client/snd_file.c:276: error: expected ‘;’ before ‘samples’
client/snd_file.c:277: error: ‘vorbis_info’ undeclared (first use in this function)
client/snd_file.c:277: error: ‘vi’ undeclared (first use in this function)
client/snd_file.c:278: error: ‘OggVorbis_File’ undeclared (first use in this function)
client/snd_file.c:278: error: expected ‘;’ before ‘vf’
client/snd_file.c:298: error: ‘vf’ undeclared (first use in this function)
client/snd_file.c:298: error: ‘ovbfr_callbacks’ undeclared (first use in this function)
client/snd_file.c:306: error: ‘samples’ undeclared (first use in this function)
client/snd_file.c:343: error: ‘OV_HOLE’ undeclared (first use in this function)
client/snd_file.c:346: error: ‘OV_EBADLINK’ undeclared (first use in this function)
make[1]: *** [release/client/snd_file.o] Error 1
make[1]: Leaving directory `/home/yasas/Desktop/alienarena7_32/source'
make: *** [build-release] Error 2


```

please, need a help here. i really like to give a try to this game.

---

### Post by yasasflash on 2009-12-05
any one??

---

