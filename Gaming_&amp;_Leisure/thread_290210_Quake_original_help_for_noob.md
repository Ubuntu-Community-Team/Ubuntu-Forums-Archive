---
title: "Quake original help for noob"
date: 2006-10-31
forum: Gaming &amp; Leisure
---

### Post by damaged on 2006-10-31
I have quake original on CD and I have looked around google but only find howtos that don't seem to work. I have found sites that talk about equake and fuhquake - but what are they? I don't want to play quake online I just want to play the original game.

Can someone help me by telling me the best way to get it running on Dapper? Or at least point me in the direction of a guide that is complete and works that would be easy enough for a noob to understand.

---

### Post by i0h on 2006-11-01
EDIT*

you probably search for JoeQuake or something like that..

---

### Post by amo-ej1 on 2006-11-01
and what's wrong with glquake ?

[http://mfcn.ilo.de/glxquake/](http://mfcn.ilo.de/glxquake/)

---

### Post by damaged on 2006-11-01
The problem I've encountered with that howto is that it refers to pak0.pak and pak1.pak files which I don't have. I assume they are meant to be from the Quake CD, but they aren't on my disc.

Any ideas?

---

### Post by bagofchickens on 2006-11-01
> **damaged said:**
> The problem I've encountered with that howto is that it refers to pak0.pak and pak1.pak files which I don't have. I assume they are meant to be from the Quake CD, but they aren't on my disc.

Any ideas?

pak0.pak and pak1.pak are on your disc. If you are at least vaguely familiar with the command line you could get them in no time. First install lha:

```
sudo apt-get install lha
```

Make some empty directory, e.g.:

```
mkdir ~/Games/quake1
```

cd to it:

```
cd ~/Games/quake1
```

Assuming your quake1 CD is already mounted, you should have in it q101_int.1 and q101_int.2 (or quake101.1 and quake101.2 depending on you version). Concatenate them by:

```
cat /path_to_cdrom/q101_int.1 /path_to_cdrom/q101_int.2 > quake.1
```

Now that you have quake.1, type:

```
lha e ./quake.1
```

After this pak0.pak and pak1.pak could be located in ~/Games/quake1/id1

---

### Post by damaged on 2006-11-01
Bagofchickens: Thanks you very much. I've never seen this in any of the howtos so far. They all just assume that I already have those files available. I would have had no idea how to get access to them and don't really follow what you did. But I can cut and paste and it worked just fine.

Thank you very much! :-D :-D :-D

---

### Post by iam_foo on 2006-11-05
i did:

$ sudo apt-get install quake2 quake2-data

then copied the pak 0,1,2 files into ./quake2

:twisted:

---

