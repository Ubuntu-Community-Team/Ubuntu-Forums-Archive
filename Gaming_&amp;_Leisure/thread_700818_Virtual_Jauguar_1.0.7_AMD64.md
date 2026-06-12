---
title: "Virtual Jauguar 1.0.7 AMD64"
date: 2008-02-18
forum: Gaming &amp; Leisure
---

### Post by RemmyLee on 2008-02-18
A system that seems to get overlooked quite often is Atari's Jaguar, so I grabbed the old SDL port and fixed the code up to get it to compile for 64 bit systems.

[Here you go.]("http://uploader.polorix.net//files/1104/virtualjaguar-1.0.7AMD64-src.tar.gz")

Don't expect too much. It is pretty slow. If I ever get some free time, I'll take a look at it a bit closer. Getting it to compile just required a few modifications and a few tweaks/optimizations to the makefile.

A couple of pointers. BIOS files shouldn't be needed as it's emulated, so just:

./vj game.bin

Notice the bin extension. It is important. It doesn't like the JAG extension, so you may need to rename some games.

The config file should be self explanatory.

---

### Post by TheRipper on 2008-03-01
Can you please upload the tarball again, or somewhere else, the link is broken... I would really like to try this emu... thx.

---

### Post by TheRipper on 2008-03-03
The link is still broken... :( Anyway, with your changes is it possible to compile with gcc-4.2? I read this on "official" forum -> [http://forums.ngemu.com/sdlemu-official-discussion/56448-official-virtual-jaguar-sdl-v1-0-7-thread-2.html](http://forums.ngemu.com/sdlemu-official-discussion/56448-official-virtual-jaguar-sdl-v1-0-7-thread-2.html)
There will be update in future... soon I hope so...

---

