---
title: "pbweb.x86"
date: 2005-07-09
forum: Gaming &amp; Leisure
---

### Post by eMuNiX on 2005-07-09
Trying to update punkbuster.  I have downloaded pbweb.x86 to my /usr/local/games/quake3/pb folder and tried to run it:- sudo sh ./pbweb.x86 no joy get an error cannot execute binary file.  Any pointers, never had a problem running this in SuSE or Yoper.

---

### Post by Yagisan on 2005-07-10
```
chmod +x pbweb.x86
./pbweb.x86
```

---

### Post by eMuNiX on 2005-07-10
Had already chmod 777 on that file which I thought was the same.  Anyway running now thanks.

---

### Post by equilibrium on 2005-07-10
have you tried putting it into ~.q3a/pb/pbweb.x86

That's where mine is :)

Or do as I did and create a symbolic link from the main quake3 folder to ~.q3a/  :grin: 

Makes it a little easier.

---

### Post by jdodson on 2005-07-10
yep.  i was messing around with pbweb.x86 for a week until i read a thread somewhere that said you needed to update your personal .q3a directory and not the main one...... doh!

---

### Post by Yagisan on 2005-07-10
[QUOTE=eMuNiX]Had already chmod 777 on that file which I thought was the same.  Anyway running now thanks.[/QUOTE] OK, I just went for the obvious first, because that was all I needed to do with Enemy Territory.

---

