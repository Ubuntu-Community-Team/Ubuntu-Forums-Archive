---
title: "Make nautilus queue file operations"
date: 2008-05-07
forum: Desktop Environments
---

### Post by DToNAToR on 2008-05-07
When I try to copy a file to some place and then try to copy another to the same place while the first one is still being copied, I want nautilus to queue the second process instead of driving the disk crazy with unnecessary disk operations ...

How do I do that?

---

### Post by Awalton on 2008-05-07
We currently do not support queuing file operations. So the answer is "You patch libnautilus/nautilus-file-operations.[ch] to do this, then post the patch on GNOME bugzilla or the nautilus mailing list for review."

---

### Post by wolfie2x on 2008-10-28
anybody know of any tool that will do queued copying?

---

### Post by wolfie2x on 2008-10-28
just tried this tool and it works nicely for queued copying of files..

[http://a.courreges.free.fr/projets/minicopier/minicopier-en.php](http://a.courreges.free.fr/projets/minicopier/minicopier-en.php)

---

### Post by Baneblade on 2009-07-15
I cant believe that this still hasn't been implemented yet.
There are thousands of votes on Brainstorm for this!
Even Windows has this functionality! (3rd party app naturally.. at this point i'm convinced that a basic install of Windows is USELESS)
But i digress.. Please dev team, we all want built in File Operations queue system. Please?

---

### Post by TBerk on 2009-11-21
Bumpity.

Ububtu 9.10 is out now with more on the Horizon. Is it time yet?

I'm currently looking for a replacement to nautilus for this very reason.


berk

---

### Post by mulp on 2010-11-24
any news on this one?

---

### Post by Rubicon421 on 2011-03-14
BUMP!  Anyone found a good solution for this yet?

---

### Post by OpenTangent on 2011-04-27
Is there some kind of technical problem with implementing this? Is it that developers just don't need to queue copy operations for whatever reason? I don't understand why this would not be a standard feature by now.

---

### Post by Rubicon421 on 2011-05-06
I'd rather find a solution that can be incorporated into Nautilus, but here's a few alternative file copiers that have queuing.

[http://ultracopier.first-world.info/](http://ultracopier.first-world.info/)
[http://www.adriancourreges.com/projects/minicopier/](http://www.adriancourreges.com/projects/minicopier/)

---

### Post by con-f-use on 2011-07-20
Wow, it's just incomprehensible why this hast not been implemented jet.

---

### Post by Deichscheich on 2012-01-31
half a year later ... still waiting for someone to explain why this is so damn hard to implement. I always feel ungrateful when asking this, since I have no coding exp myself, but seriously, this feature would warrant a complete re-write of nautilus if it is impossible to do with the current code base.

---

### Post by PiK4cHu on 2012-02-10
Just my 2cents : dolphin (file browser from KDE) has pause but not queue management, though.

Still, it's a big part of what made me switch to Kubuntu. :KS

I remember voting for it in ubuntu brainstorm, can't find it now ; well, if you find it, I trust you can get a snippet of the idea to embed on your blog/whatever and lobby for it !

---

### Post by Sonja on 2012-05-11
To avoid a complete rewrite of Nautilus, maybe Nautilus can just warn you "You are already in the middle of a big file copy. Are you sure you want to copy these simultaneously?" and teach the user to be patient.

---

