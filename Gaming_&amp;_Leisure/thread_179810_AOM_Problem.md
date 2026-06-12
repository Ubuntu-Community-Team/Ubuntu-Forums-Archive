---
title: "AOM Problem"
date: 2006-05-20
forum: Gaming &amp; Leisure
---

### Post by thunderduck3141 on 2006-05-20
hi all
i just put cedega together from cvs and now i am trying to install age of mythology
i cant get past the cd-key thing (i AM using a valid key) and i own the game so nothing illegal going on here... at least not now:twisted: 
problem is, when i click "Next" after entering the cd-key, it say

Setup cannot load the file PidGen.dll

somebosy please help me
(im using Dapper)

---

### Post by WildPenguin on 2006-05-20
If I recall correctly you will need to copy PidGen.dll from the CD to the virtual 'C:\windows\system' folder created by Cedega.

I was able to get AOM running once under Cedega, however preformance was poor, and the majority of the text was broken. Tell us if you have any better success.

---

### Post by Harleen on 2006-05-20
I only tried it with plain wine, not Cedega, so this might not apply to you.
I also had the message at that point, that this dll couldn't get loaded. The reason was, that this dll tries to load the mfc42.dll (or the like), which wasn't present on my wine install.

---

### Post by Bohlio on 2007-08-06
I know this is reviving an incredibly old thread, but for those of you who googled the problem, you've found this and there isn't an exact solution to the problem unless you visit a few places and put the peices together. Apparently this is a problem with Halo also.

The solution is to add PidGen.dll *AND* mfc42.dll to the wine system32 folder. 
I hope this has helped someone :D

---

