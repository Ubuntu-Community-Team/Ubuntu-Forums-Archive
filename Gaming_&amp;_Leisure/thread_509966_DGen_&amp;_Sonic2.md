---
title: "DGen &amp; Sonic2"
date: 2007-07-26
forum: Gaming &amp; Leisure
---

### Post by Sluipvoet on 2007-07-26
Dgen(Sega Genesis/MegaDrive emulator) can't play my favourite game Sonic2, it just freezes after a few seconds.
Is there anything that can be done about this.

PS I own a legitimate copy of Sonic2 and a MegaDrive, so there is nothing illegal about this question.
PS2 I now Sonic2 works well with Gens, but I prefere Dgen.

---

### Post by DoktorSeven on 2007-07-26
Not sure what to tell you; dgen + Sonic 2 works perfectly here, if a bit slow and choppy (which I blame on dgen, since OpenGL Gens runs it just fine).

If you run dgen from a terminal prompt, does it spit out anything interesting after it freezes?

---

### Post by chips24 on 2008-03-02
i really want to play "Sonic 3 and knuckles" can you help me find dgen and the game and help me install them?
I get the same error with dgen when i play sonic 2, and i have been trying to install gens from source, but i get this error...

make[3]: Entering directory `/home/caleb/gens-2.15.5/src/gens'
mkdir -p gens_core/gfx gens_core/io gens_core/mem gens_core/misc gens_core/sound gens_core/cpu/sh2 gens_core/vdp gens_core/cpu/z80 ;
nasm -O1 -D __GCC2 -f elf -I./gens_core/ -I./gens_core/io/ -I./gens_core/misc/ -I./gens_core/vdp/ -I./gens_core/sound/ -I./gens_core/gfx/ -I./gens_core/cpu/sh2/ -I./gens_core/cpu/z80/ -I./gens_core/mem/ gens_core/gfx/blit.asm -o gens_core/gfx/blit.o
/bin/bash: nasm: command not found
make[3]: *** [gens_core/gfx/blit.o] Error 127
make[3]: Leaving directory `/home/caleb/gens-2.15.5/src/gens'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/caleb/gens-2.15.5/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/caleb/gens-2.15.5'
make: *** [all] Error 2

---

