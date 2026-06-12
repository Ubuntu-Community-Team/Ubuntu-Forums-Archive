---
title: "help with epsxe"
date: 2007-03-23
forum: Gaming &amp; Leisure
---

### Post by Nolander on 2007-03-23
i installed Epsxe by following a HOWTO but now its not working.

when i go file -> Run CDROM i get:
```
 * Running ePSXe emulator version 1.6.0.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [bios/SCPH1001.BIN].
 * Init internal cdrom ... ok
 * First/Last track: 1 2
 * Track 1:  (DATA) - Start 0: (00,02,00)
 * Track 2:  (AUDIO) - Start 1: (38,27,55)
 * PAL cdrom detected.
 * Init gpu[0][libgpuPeopsSoftX.so.1.0.17]
 * Open gpu[0]
plugins/libspu.so: cannot open shared object file: No such file or directory

```

then the teminal and program terminates

help Plz!

ta Nolander

---

### Post by rolando2424 on 2007-03-23
You must be trying to use a sound plugin that you don't have installed.

Open the Terminal, go to the epsxe folder, open the plugin folder in there and type "dir".

Then paste here what the console output. :D

---

