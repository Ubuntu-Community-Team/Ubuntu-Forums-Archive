---
title: "Uninstall Wolfenstein: Enemy Territory &amp; True Combat: Elite"
date: 2008-08-21
forum: Gaming &amp; Leisure
---

### Post by taamir on 2008-08-21
I installed the 2 games but Having problems With playing and downloading maps..
eventually I decided to uninstall them.
But I don't know how,
I have an uninstall file in:

/usr/local/games/enemy-territory/uninstall.run

but i cant get it to work.

and I need a way that will clear all the installed files from the directory above and from 

/home/gilad/.etwolf (<- this one with a Lock on it)

and if there are more files installed them also..

Thx 

Taamir

---

### Post by linuxguymarshall on 2008-08-21
First of all I was having trouble installing maps too, its because your running an old version just upgrade. But if you really want to uninstall just do this 

```
cd /usr/local/games/enemy-territory
```


then 

```
sudo sh uninstall.run
```

---

### Post by taamir on 2008-08-22
1. HI I have version 2.60, How do I upgrade?
2. I Wanted to uninstall because I need to use "SUDO" command for running the game and I was told its Risky..

---

### Post by taamir on 2008-08-27
I try yo uninstall but I get this Message :

```
gilad@Gilad-Desktop:/usr/local/games/enemy-territory$ sudo sh uninstall.run
sh: Can't open uninstall.run

```

Please help

---

### Post by jmtdstoc on 2008-08-27
On the same folder as before, try to run:

```
sudo ./uninstall.run
```

Does this work?

---

### Post by Evil Wayz on 2008-08-31
sorry to hijack, but I can't find a place to download et 2.6 or tce .49b in linux anywhere, anyone reccomend a torrent or a mirror?

---

### Post by taamir on 2008-08-31
NP
you can find downloads and instructions on this site:

[http://tce.helpz0r.net/instlin1.html](http://tce.helpz0r.net/instlin1.html)

---

