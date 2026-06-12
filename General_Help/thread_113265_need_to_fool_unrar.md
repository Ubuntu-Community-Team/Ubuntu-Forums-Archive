---
title: "need to fool unrar"
date: 2006-01-06
forum: General Help
---

### Post by uberlinux on 2006-01-06
I need to get a rared video file to unrar.  the download is stuck at 99% which will make the RAR fail its stupid CRC check, like so:
```

pest@blustation:~/Junk/Over There Season 1/Episodes$ unrar e -av- Over\ There\ S1\ E10\ -\ Suicide\ Rain.rar

RAR 3.30    Copyright (c) 1993-2004 Eugene Roshal    22 Jan 2004
Shareware version         Type RAR -? for help


Extracting from Over There S1 E10 - Suicide Rain.rar


Over There S1 E10 - Suicide Rain.avi already exists. Overwrite it ?
[Y]es, [N]o, [A]ll, n[E]ver, [R]ename, [Q]uit Y

Extracting  Over There S1 E10 - Suicide Rain.avi                       2%
Over There S1 E10 - Suicide Rain.avi - CRC failed
Total errors: 1

```
I need to make it override its CRC check.
anyone?
thanks

---

### Post by sciurus on 2006-01-06
The flags -av- Disable AV check and -kb Keep broken extracted files sound promising.

---

