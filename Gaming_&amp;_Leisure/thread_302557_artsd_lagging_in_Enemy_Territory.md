---
title: "artsd lagging in Enemy Territory"
date: 2006-11-18
forum: Gaming &amp; Leisure
---

### Post by willhurt on 2006-11-18
Hi im runnig et with this script;
```

#! /bin/sh

killall -9 esd
artsd  &
cd /usr/local/games/enemy-territory
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
exec artsdsp -m ./et.x86 "$@"

killall -9 artsd

```

which gives me sound but i get about 1/2 a second lag, is there a way in ubuntu [gnome] to reduce artsd's latency. Ive seen a few posts that tell people to change stuff in system settings but this is for KDE. 

Ive had alook at the output of artsd -h but i dont understand that too much?

Thanks

---

