---
title: "getting amarok to play mp3"
date: 2006-08-29
forum: Desktop Environments
---

### Post by DMAthlon on 2006-08-29
I would really like to use amarok to play my mp3 files but unfortunately it wont. it appears to have the same kind of library organization as windows media player which i am fond of.

i dont really want to convert them all to OGG and take up twice the space just so windows can play them as well. is there anythign i can do?

---

### Post by Jagot on 2006-08-29
Ubuntu and it's derivatives do not come with mp3 support by default.  You'll need to enable the multiverse repository using either of these methods:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

Then, from Terminal:

```
sudo aptitude update
sudo aptitude install libxine-extracodecs
```

---

