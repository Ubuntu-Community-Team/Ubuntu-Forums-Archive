---
title: "CD emulation software"
date: 2005-01-18
forum: General Help
---

### Post by node on 2005-01-18
Is there anything like daemon tools or alcohol 120% for linux ?

---

### Post by rivasdiaz on 2005-01-18
[QUOTE=node]Is there anything like daemon tools or alcohol 120% for linux ?[/QUOTE]

Not needed. You can mount an ISO image directly with mount.

I'm not logged in linux right now, but you need to do something like this:
$ mount <iso image> <path to mount> -o loop

example:
$ mount myisoimage.iso /media/tmp -o loop

help:
$ man mount

Rivas

---

### Post by node on 2005-01-18
I have a BIN and CUE file ;)

---

### Post by randy on 2005-01-18
Check the universe for an app that will convert from a bin/cue to an iso.

---

