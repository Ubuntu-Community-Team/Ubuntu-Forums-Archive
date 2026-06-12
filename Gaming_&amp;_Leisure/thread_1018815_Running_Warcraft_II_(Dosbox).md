---
title: "Running Warcraft II (Dosbox)"
date: 2008-12-22
forum: Gaming &amp; Leisure
---

### Post by Mila on 2008-12-22
So technically this doesn't belong in the Wine subcategory since, well, Warcraft II is a DOS game and doesn't run in Wine.

Anyway, I'm trying to install and run Warcraft II. The original 1995 version, not the later Battle.net edition. So I downloaded DOSBox, configured it, and installed Warcraft. It loads and everything, but every time I try to play single player it tells me that I need to insert my cdrom or I can't do it. 

I tried mounting the cdrom in DOSBox like this:
```
mount d /media/cdrom -t cdrom
```

But I still got the same error ingame. I also tried:
```
mount d /media/cdrom0 -t cdrom
```

And still got the same error ingame. Then I tried copying the contents of the CD to the harddrive and then mounting that folder as a cdrom like:
```
mount d ~/war2cd -t cdrom
```

... and that didn't work either. Is there something glaringly obvious that I am missing? Has anyone else had this issue?

Mila

---

### Post by disturbedite on 2008-12-22
i know i'm not directly addressing your issue, but last time i checked, warcraft 2 bne worked fine with wine. i'd recommend getting the bne.

---

### Post by Mila on 2008-12-22
> **disturbedite said:**
> i know i'm not directly addressing your issue, but last time i checked, warcraft 2 bne worked fine with wine. i'd recommend getting the bne.

I considered that, but about a year ago I managed to get this version to run properly with DOSBox on XP. And I'd rather not buy another version of the game when I know that the one I have works perfectly well.

Additionally it kinda works (except for sound) if I run Warcraft II in DOSBox in Wine but that kinda seems a bit, well, kooky. I'd like to get it working in DOSBox on Linux.

---

### Post by Mila on 2008-12-22
Since I just figured it out and got it working, I figured I'd share just in case anyone else has the same weird problem.

When I insert the CD, Ubuntu (for some odd reason) thinks it's both an audio cd *and* a software cd. So in my /media/ directory it mounts *two identical cds*, CDROM and CDROM0.

So in DOSBox, I have to mount both versions. That is:
```
mount d /media/cdrom -t cdrom
mount e /media/cdrom0 -t cdrom
```

If I only do one or the other, Warcraft doesn't recognize as there being a CD, but if I do *both* it works.

---

### Post by disturbedite on 2008-12-23
that may be cuz the game is a mixed mode/multisession disc.

---

### Post by mikedep333 on 2008-12-23
There is also wargus. It is a rewrite of the warcraft 2 engine, set to use the data from the old dos warcraft 2. It adds enhancements like higher resolutions.

[http://wargus.sourceforge.net/](http://wargus.sourceforge.net/)

I'm not sure how to install it on ubuntu 8.04 or 8.10 however.

---

