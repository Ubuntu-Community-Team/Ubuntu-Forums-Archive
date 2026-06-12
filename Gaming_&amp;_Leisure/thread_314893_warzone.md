---
title: "warzone"
date: 2006-12-08
forum: Gaming &amp; Leisure
---

### Post by Pathfinder_ on 2006-12-08
hi, i just installed warzone using the loki installer and when i try to run it i get this error:
```
./warzone.bin: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory
```
what should i do to fix it?
btw, i tried google and it didn't help

---

### Post by Perfect Storm on 2006-12-08
As the error said, you need libpng lib to make it work. So you have to install libpng;
```
sudo aptitude install libpng12-0
```

If that the case you have libpng installed and the error shows up, the chance is because it have another name on ubuntu. Solution is to make a symblink;
```
sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.3
```

---

### Post by Pathfinder_ on 2006-12-08
i made the symlink and it started. ty
however, when i try to play singleplayer/tutoral/campaign the game exits and i get this:
```
warzone.bin: r200_vtxfmt.c:1047: r200VtxFmtFlushVertices: Assertion `rmesa->dma.flush == 0 || rmesa->dma.flush == flush_prims' failed.
./warzone: line 124:  4804 Aborted                 (core dumped) ./${GAME_BINARY} ${CMD_ARGS} "$@"

```

---

