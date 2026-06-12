---
title: "UT2004 on Karmic 9.10 x64 - need libopenal.so.0 file"
date: 2009-10-31
forum: Gaming &amp; Leisure
---

### Post by automaton26 on 2009-10-31
I've moved to a fresh install of Kubuntu 9.10 **x64**, and I'm trying to get UT2004 working (I know, but I'm still addicted to it !)

I've got to the point where the game runs fine, but sound is still not working.

I can recreate the missing *libopenal* link with:

```
cd /usr/local/games/ut2004/System
sudo ln -s /usr/lib/libopenal.so.0 libopenal.so.0

```
but this points to a missing (amd64?) /usr/lib/libopenal.so.**0** file, because Karmic only ships with /usr/lib/libopenal.so.**1**.

I'm still a bit new to locating/building packages, so if anyone could point me in the right direction I'd be grateful.

Thanks.





/*************************************************/

[SIZE="1"]
UPDATE: How I got UT2004 working on Karmic 9.10 x64:

1) Run the normal UT2004 installer (you can use your file manager app to mount/unmount multiple CDs during install):
```

sudo /media/cdrom/linux-installer.sh
exit

```

2) Fix the folder permissions:
```
cd /usr/local/games
sudo chmod -R 0777 ut2004

```

3) Create a "*/usr/local/games/ut2004/System/cdkey*" file that contains your CD key.

4) Resolve this missing library:
```

cd ~
wget http://fr.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_amd64.deb
sudo dpkg -i ~/libstdc++5_3.3.6-17ubuntu1_amd64.deb

```

5) Resolve missing library links:
```

cd /usr/local/games/ut2004/System
sudo ln -s /usr/lib/libSDL-1.2.so.0 libSDL-1.2.so.0
sudo ln -s /usr/lib/libopenal.so.1 openal.so

```
[/SIZE]

---

### Post by Rhubarb on 2009-10-31
I successfully got UT2004 working in 64bit ubuntu around a year or so ago - and that was missing an openal package that only existed in a version of ubuntu before that!

Anyway, I haven't tested this out (I haven't played UT2004 in quite a while) recently, certainly not on Karmic.

You could try getting an old version of libopenal from here:
[http://packages.ubuntu.com/dapper/amd64/libopenal0/download](http://packages.ubuntu.com/dapper/amd64/libopenal0/download)

And see if that works.

I've got my UT2004 DVD here ... maybe I should start playing again :D

---

### Post by automaton26 on 2009-10-31
Thanks for that - I had it working in Jaunty x64 last week (straight from install with no problems).

Anyway, I've just tried:

```
wget http://fr.archive.ubuntu.com/ubuntu/pool/universe/o/openal/libopenal0_0.2005080600-2.1build2_amd64.deb
sudo dpkg -i libopenal0_0.2005080600-2.1build2_amd64.deb

```

...and that had a further dependency on:
```
wget http://fr.archive.ubuntu.com/ubuntu/pool/main/a/arts/libartsc0_1.5.2-0ubuntu1_amd64.deb
sudo dpkg -i libartsc0_1.5.2-0ubuntu1_amd64.deb

```

...but still no sound - so near yet so far !

Perhaps I need a different 0.X.X version, rather than that 0.0.8 ?

---

### Post by automaton26 on 2009-10-31
Resolved :D

The library link should be called *openal.so*, not *libopenal.so.0*.

```
sudo ln -s /usr/lib/libopenal.so.**1** openal.so
```

So I've updated the guide (at the end of my original post) to match it.

---

### Post by Rhubarb on 2009-10-31
> **automaton26 said:**
> Resolved :D

The library link should be called *openal.so*, not *libopenal.so.0*:

```
sudo ln -s /usr/lib/libopenal.so.0 openal.so
```

So I've updated the guide (at the end of my original post) to match it.

See you all online (although the UT2004 master server has gone down, perhaps for good?)

Sweet :)
That's good to know how to get it working, still good for LAN games ;)

---

### Post by automaton26 on 2009-10-31
Also (!) I've now found that it's OK to link it to */usr/lib/libopenal.so.**1*** instead of */usr/lib/libopenal.so.**0***. Otherwise the sound doesn't sync properly.

I've amended the original post (again).

---

