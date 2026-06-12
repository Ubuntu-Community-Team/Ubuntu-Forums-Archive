---
title: "World Of Warcraft - Run in wine without reinstall?"
date: 2009-03-11
forum: General Help
---

### Post by GCoffee on 2009-03-11
Hey,

I want to run WoW (World Of Warcraft) under wine on ubuntu 8.10, however im not particulary keen on re-downloading all the 8gb or so of patches.

I can access my windows (NTFS) drive on ubuntu and was wondering if it is possible just to run it from there without a reinstall?

I will be using the latest version of wine & WoW.

GCoffee.

---

### Post by GCoffee on 2009-03-11
bump.

Plz someone some advice. do i just need to move A dll file or something..?

---

### Post by cb951303 on 2009-03-11
it's possible in fact it works better this way. But you may have to copy the files over your linux partition (not sure about it though, it may very well work from NTFS partition too)

---

### Post by hallbrian on 2009-03-11
You ca run WoW under wine without installing anything on your ubuntu system, as long as it is installed on windows its fine.

just terminal to you wow dir and run this command

```
wine /media/winpartiton/World\ of\ Warcraft/wow.exe -opengl
```

should work fine.

You could aslo make icon with the above command in, so dont have to run terminal every time..

Cheers
Brian

---

