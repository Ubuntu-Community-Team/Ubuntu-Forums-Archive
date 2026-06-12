---
title: "similar prog to daemons tools in linux?"
date: 2006-02-03
forum: Desktop Environments
---

### Post by zeltak on 2006-02-03
Hi

as a long time windows (Yuck) user one of the most used programs there was daemons tools. Ive looked for something similar (with a simple GUI interface) in Linux but with no luck. Can anybody reccomend a program similar to daemons tools?

thx alot

Zeltak

---

### Post by audax321 on 2006-02-03
Well, it depends on what your trying to do. You can mount and access the contents of iso, img, and nrg files (as well as others) in Linux easily without any software or "hacking". But, to emulate an actual drive requires some work... I've never done it and have never had a need to emulate a drive, but Google should bring some information about that.

Here is how to mount some file:

ISO/IMG:
```
sudo mount -r -o loop /path/to/iso /path/to/directory_for_mount
```

NRG:
```
sudo mount -r -o loop,offset=307200 /path/to/iso /path/to/directory_for_mount
```


If you prefer the right-click way of doing it, take a look here: [http://kdelook.org/content/show.php?content=11577](http://kdelook.org/content/show.php?content=11577)

---

