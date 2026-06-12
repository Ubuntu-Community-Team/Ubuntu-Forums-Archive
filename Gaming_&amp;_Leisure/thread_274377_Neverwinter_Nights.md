---
title: "Neverwinter Nights"
date: 2006-10-09
forum: Gaming &amp; Leisure
---

### Post by parradux on 2006-10-09
I'am having a problem running the game. 

I downloaded the client from the bioware site, and patched it. However, when I execute the command ./nwmain I am presented with this error: 

./nwmain: error while loading shared libraries: libmss.so.6: cannot open shared object file: No such file or directory

How can I fix this and get this game to run?

---

### Post by ZylGadis on 2006-10-09
./nwn

---

### Post by Perfect Storm on 2006-10-10
A good idea will be making a launcher script for NWN so you don't have to navigate to NWN folder to start the game.

```
cd /into/NWN/folder
nano LaunchNWN.sh
```

add:

[b]#!/bin/bash

cd /into/NWN/folder
./nwn
[/b]

```
chmod +x LaunchNWN.sh
```


save <ctrl> + <o> and exit <ctrl> + <x>

Now you can make launcher/shortcut pointing to LaunchNWN.sh
eg: **sh /blah/blah/blah/LaunchNWN.sh**

---

