---
title: "jedi academy  help/question"
date: 2007-09-18
forum: Gaming &amp; Leisure
---

### Post by Phobia on 2007-09-18
Question:First: Is their a way to run Jedi Knights 3 with out  using Wine/X?
 on linux gamers web site there was a link to an linux installer. But it brings up 404 page not found. Is the installer still around?

Second:  when installing with wine the game keeps asking for the CD even when i start  it for the disk. I did a winecfg and  made it see my cd-rom as cd rom and not hd. So has any one had this problem or knows how to fix it?





--Thanks

---

### Post by mattskr on 2007-09-18
try 

```
wine eject d:
```

or whatever your CD-drive is in wine. MAKE SURE that Ubuntu mounts your CD before clicking Ok when installing your game. Wine will not be able to see the CD until Ubuntu mounts it.

---

### Post by cogadh on 2007-09-18
The installer was an installer that made use of Wine to run the game's executable, so no, it cannot be run without Wine (or CrossOver or Cedega).

As for the disk detection problem, that can sometimes be fixed by creating a symlink to your CD-ROM drive's device entry in Wine's dosdevices directory. Otherwise, you may need to use a cracked exe to get around the problem.

---

