---
title: "Lag Spikes in CS 1.6"
date: 2006-10-30
forum: Gaming &amp; Leisure
---

### Post by Kimm on 2006-10-30
Hi

I'm playing CS 1.6 using wine 0.9.23.
The game starts and I'm able to join a server, but every 10 seconds the game lags terribly for about 5 seconds... I've tried  changing the screen res. and colour depth, I also tried setting wine to emulate a desktop and to emulate Vertex Shaders, nothing seems to help...

Could this be caused to some background process? I'm using Xubuntu Edgy (installed from Ubuntu using apt-get, and has been dist-upgraded).

My RAM is somewhat obscure, but its 256 MB
Intel Celeron 1.7 Ghz
NVIDIA FX5500 128Mb
10 mbps Fiberoptic internet connection...

Has anyone else had this problem? Can someone help out... its VERY disturbing, since these 5 seconds can mean life or death in-game...

Edit: Just though I'd point out that I'm using OSS audio for Wine and I'm using this script to start CS:

```

#!/bin/bash
WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe -fullscreen \
    -width 1024 -height 768 -applaunch 10 \
    -heapsize 64000 -gl

```

---

### Post by Kimm on 2006-10-30
Fixed:

It was a background process.
I killed apt-index-watcher and everything became fine.

---

