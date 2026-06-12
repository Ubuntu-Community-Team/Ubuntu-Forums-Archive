---
title: "Installing tar.xz game (libGLU.so)"
date: 2016-06-08
forum: Gaming &amp; Leisure
---

### Post by janat08 on 2016-06-08
Unpacked the game, running sh start.sh results in:
start.sh: 2: cd: can't cd to start.sh
./hoi4: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory

start.sh:
#!/bin/bash
GAMEDIR=$(cd "${0%/*}" && echo $PWD)
cd "$GAMEDIR"
export LC_ALL=C
exec ./hoi4 "$@"

---

### Post by X-RED_Tech on 2016-06-08
What game? Obtained from where?

---

### Post by deadflowr on 2016-06-08
*Thread moved to **Gaming & Leisure**.*

---

### Post by janat08 on 2016-06-08
It were a Hearts of Iron 4 from the piratebay.

---

### Post by QIII on 2016-06-08
Pirate Bay?  We do not condone circumvention of copyrights or intellectual proprty rights or software piracy. 

Closed.

---

### Post by bapoumba on 2016-06-08
And thread closed, please have a look at our posting rules, thanks : [http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)

---

