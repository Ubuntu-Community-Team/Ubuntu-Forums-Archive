---
title: "Gimp Crash"
date: 2005-07-28
forum: Desktop Environments
---

### Post by rathel on 2005-07-28
When ever I try and save something with The Gimp it crashes. I ran it from terminal and get this error:
```

(script-fu:11633): LibGimpBase-WARNING **: script-fu: wire_read(): error
Segmentation fault

```
How do I fix this? Thanks in Advanced.

---

### Post by hydra on 2005-07-28
this is due to the version of the gtk-qt-engine ur using...first note the CVS version  and then installl the latest igtk-qt-engine

this should work [ gtk-qt-engine-0.41-6.i386.rpm](http://fedoraproject.org/extras/4/i386/repodata/repoview/gtk-qt-engine-0-0.41-6.html)

ITS weird ur having this prb most SUSE users have, anyways....

hope it helps

---

### Post by rathel on 2005-07-28
Thanks, that helped alot! now I can finally save.

---

