---
title: "Punkbuster problems in Quake 3?"
date: 2005-12-12
forum: Gaming &amp; Leisure
---

### Post by arcanistherogue on 2005-12-12
So, I installed quake 3 from my windows copy by making quake3/baseq3 then installing the latest point release and putting the pak file in the right place.

Then, I did that sound patch thing for breezy, and played a couple rounds wiht bots.  When I wanted to play online, it said I didn't have the latest edition of punkbuster.

So, after googling I found this pbweb.x86 file to put in ~/.q3a/pb then execute it.  I do that, and still I get punkbuster errors when joining servers. 

I also do this in /usr/local/games/quake3/pb just to be sure, and then I went to browse servers again.

Well, anyway, I check and I see that Punkbuster is listed as Disabled.  I try to enable this, but it still says disabled.  I enabled it like 10 times, and restarted quake a lot of times also, but it still says disabled.

Did I do something wrong?  How do I fix this?

---

### Post by miscz on 2005-12-13
Check the Punkbuster's permissions, I haven't played Q3 for a long time but I think it was the cause of most PB problems.

---

### Post by arcanistherogue on 2005-12-13
How do I do this?  What I did was 

```
sudo chmod -R 777 /usr/local/games/quake3/pb
```

and it still will not work.  Is that what you meant by permissions?

---

### Post by arcanistherogue on 2005-12-14
bump

---

### Post by miscz on 2005-12-14
Do you still have PB in ~/.quake3? If so try checking it's permissions too / deleting it. If this doesn't help, google. ;)

---

### Post by Orunitia on 2006-03-13
I'm having the same problems. Hopefully someone has an actual solution.

---

### Post by arcanistherogue on 2006-03-13
Funny actually, when I saw this as the most recent post I said to myself "Hey, I swore I had that same problem a couple months ago..."

---

### Post by Orunitia on 2006-03-14
:P


Well did you ever actually get it fixed? If so, how?

---

### Post by Orunitia on 2006-03-14
Nevermind I think I fixed it. I found out there was a /.q3a folder, and deleted punkbuster from there.

Yay I can play quake 3. :D

---

