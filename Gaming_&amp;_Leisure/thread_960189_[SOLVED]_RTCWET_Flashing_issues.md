---
title: "[SOLVED] RTCW:ET Flashing issues"
date: 2008-10-27
forum: Gaming &amp; Leisure
---

### Post by plasmarox on 2008-10-27
Hello, im running Ubuntu Hardy Heron, and i've installed enemy territory for linux, which runs and plays technically fine as far as playability, BUT the screen flashes every second, which is incredibly an annoying.

Any body got any ideas on how to resolve?

PS my sys info is in my sig

---

### Post by Perfect Storm on 2008-10-27
Does
```
metacity --replace
```
Then, Run the game.

Does it helps?

---

### Post by plasmarox on 2008-10-27
:o thats perfect, completely sorted it!

Thanks alot, :D

---

### Post by Perfect Storm on 2008-10-27
If you don't want to run that command every time; You can use fusion-icon which are available through the repo.

Or making a script;

```
nano Launch-RTCW.sh
```

add the following;

[b]#!/bin/bash

metacity --replace &

<RTCW:ET executing command>

compiz --replace &[/b]


Save [ctrl]+[o] and Exit [ctrl]+[x]

```
chmod +x Launch-RTCW.sh
```

This script will first disable compiz then run the game. After you exiting the game it wil enable compiz again.

---

