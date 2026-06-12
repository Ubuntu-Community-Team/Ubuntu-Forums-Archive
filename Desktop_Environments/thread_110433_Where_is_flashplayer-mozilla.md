---
title: "Where is flashplayer-mozilla?"
date: 2005-12-30
forum: Desktop Environments
---

### Post by ryan76 on 2005-12-30
Hi, I'm trying to get flash working in firefox. I can't find the repository that has flashplayer-mozilla in it. This is my sources.list:

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://it.archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://it.archive.ubuntu.com/ubuntu breezy multiverse
```

it's not coming up through apt-get install or Synaptic with this sources.list.

Any help greatly appreciated!

Thanks

---

### Post by kaamos on 2005-12-30
It is in multiverse/web. Have you ran "sudo apt-get update" after making changes to the sources.list?

---

### Post by ryan76 on 2005-12-30
Yes:

```

Fetched 3B in 16s (0B/s)
Reading package lists... Done
ryan@ubuntu:/etc/apt$ sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
ryan@ubuntu:/etc/apt$

```

---

### Post by dcstar on 2005-12-30
[QUOTE=ryan76]Hi, I'm trying to get flash working in firefox. I can't find the repository that has flashplayer-mozilla in it. This is my sources.list:

```

.......
deb http://it.archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://it.archive.ubuntu.com/ubuntu breezy multiverse
```

it's not coming up through apt-get install or Synaptic with this sources.list.

Any help greatly appreciated!

Thanks[/QUOTE]
Why do you use the "it" (Italy?) repository mirror?, just make it [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) universe main restricted multiverse

---

