---
title: "Back up location"
date: 2009-03-21
forum: General Help
---

### Post by clamsd101 on 2009-03-21
I was wondering if anyone could tell me the command [like this one]("http://tinyurl.com/2copm3") that puts the tar in my host folder, where there is more space. Thanks.

---

### Post by zwanzig on 2009-03-21
I suppose you mean home folder?
Just put the path in front of backup.tgz
example for home folder:
```
tar cvpzf ~/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=~/backup.tgz --exclude=/mnt --exclude=/sys /
```

Note that the command uses the file path twice, so change at both places.

---

