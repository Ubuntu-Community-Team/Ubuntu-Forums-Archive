---
title: "UT2004 patch 3355 breaks the game"
date: 2007-04-22
forum: Gaming &amp; Leisure
---

### Post by Fangs404 on 2007-04-22
I installed UT2004 last night, and it ran just fine.  I downloaded the 3369 patch ([http://www.beyondunreal.com/main/ut2004/ut2004essential.php](http://www.beyondunreal.com/main/ut2004/ut2004essential.php)) and attempted to install it by just copying the files over.  The new files were successfully copied, but UT2004 no longer opens.  When I navigate to /usr/local/games/ut2004, all the proper files are there.  And if I try to run ut2004, I get this:

```
exec: 50: ./ut2004-bin: not found
```

ut2004-bin is certainly in the System folder where it needs to be and where it was prior to the patch.  What the crap happened to my install?  Also, I read that the mega patch might work also (since it apparently includes the 3369 patch and map updates and crap).  So I tried copying the mega patch over a new install of ut2004, and it still doesn't work.  What's going on?  I know this must be a simple solution, but I have no idea what's wrong.

---

### Post by Fangs404 on 2007-04-23
So nobody that plays UT2004 had an issue patching this guy?

---

### Post by Cappy on 2007-04-24
I installed this a couple of days ago and I ran into a similar problem on my 64-bit feisty.

[http://www.omgili.com/preview/aHR0cDovL2ZvcnVtcy5iZXlvbmR1bnJlYWwuY29tL3Nob3d0aHJlYWQucGhwP3Q9MTgyOTIz](http://www.omgili.com/preview/aHR0cDovL2ZvcnVtcy5iZXlvbmR1bnJlYWwuY29tL3Nob3d0aHJlYWQucGhwP3Q9MTgyOTIz)

$ locate ut2004-bin
/usr/local/games/ut2004/System/ut2004-bin-linux-amd64
/usr/local/games/ut2004/System/ut2004-bin

I use the ut2004-bin-linux-amd64, yours might be different

---

