---
title: "Sound Issues"
date: 2010-11-14
forum: Gaming &amp; Leisure
---

### Post by jakejw93 on 2010-11-14
I am having sound issues with enemy-territory and Americas army. Both games have no sound what so ever. Any help? thanks in advance

---

### Post by Perfect Storm on 2010-11-14
Try run the game with padsp. If it doesn't work and you can't live without them. You have two options; 1) use Ubuntu 10.04 instead of Ubuntu 10.10 or 2) compile a new kernel with enable oss support.

---

### Post by jakejw93 on 2010-11-14
That worked! :)
I wrote in the terminal:
LD_PRELOAD=/usr/lib/libpulsedsp.so [path to armyops]
The sound then worked great

---

