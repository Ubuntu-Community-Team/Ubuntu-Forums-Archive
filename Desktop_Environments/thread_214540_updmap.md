---
title: "updmap"
date: 2006-07-12
forum: Desktop Environments
---

### Post by ghotra on 2006-07-12
Coming from gentoo, I used to type

updmap --enable Map /home/myname/texmf/fonts/map/dvips/arev/arev.map

and that would be it!

I'm trying to do the same in ubuntu without much luck:

```
updmap: This is updmap, version 1107552857-debian
updmap: using transcript file `/home/myname/.texmf-var/web2c/updmap.log'
updmap: initial config file is `/home/myname/.texmf-config/web2c/updmap.cfg'
touch: cannot touch `/etc/texmf/updmap.d/10local.cfg': Permission denied
Creating new entry for map file /home/myname/texmf/fonts/map/dvips/arev/arev.map in /etc/texmf/updmap.d/10local.cfg
grep: /etc/texmf/updmap.d/10local.cfg: No such file or directory
/usr/bin/updmap: line 344: /etc/texmf/updmap.d/10local.cfg: Permission denied
Running update-updmap to merge the changed files
update-updmap: unable to determine the configuration directory; you can
specify it with --conf-dir
Now running updmap again to generate output files
updmap --cnffile=/home/myname/.texmf-config/web2c/updmap.cfg
updmap: This is updmap, version 1107552857-debian
updmap: using transcript file `/home/myname/.texmf-var/web2c/updmap.log'

updmap is creating new map files using the following configuration:

```

Anyway, the subsequent ouput never lists arev.map...and my documents never find the fonts.  What do I need to do to add new fonts?

THanks.

---

### Post by ghotra on 2006-07-13
Surely someone must know the answer.

---

