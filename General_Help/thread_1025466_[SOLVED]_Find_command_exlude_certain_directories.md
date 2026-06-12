---
title: "[SOLVED] Find command: exlude certain directories?"
date: 2008-12-30
forum: General Help
---

### Post by inselaffe on 2008-12-30
When using the find command I would like to prevent certain directories from being searched through.

Specifically, I generally connect to half a dozen or more SMB shares, which means they become mounted under ~/.gvfs. When the find command hits that folder it goes through those network share too which, whilst sometimes very useful, in many cases isn't what I'm trying to achieve but takes a long time and generates an amount of needless network traffic.

Using [FONT="Courier New"]find . ! -path './.gvfs/*'[/FONT] [from ~] does exclude everything under that path structure from the results printed to stdout, but the command still iterates through the mounted SMB shares, as it pauses at that point.

Any ideas?

---

### Post by caljohnsmith on 2008-12-30
How about trying:
```
find . -wholename '*.gvfs*' -prune -o -iname "*searchterm*"
```

---

### Post by inselaffe on 2008-12-30
> **caljohnsmith said:**
> How about trying:
```
find . -wholename '*.gvfs*' -prune -o -iname "*searchterm*"
```

That seems to do the trick. Thanks!

---

