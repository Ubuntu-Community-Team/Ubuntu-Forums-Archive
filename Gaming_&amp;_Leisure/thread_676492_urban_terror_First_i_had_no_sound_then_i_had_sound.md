---
title: "urban terror First i had no sound then i had sound and now i'ts gone again!"
date: 2008-01-23
forum: Gaming &amp; Leisure
---

### Post by wormeyman on 2008-01-23
I'm wondering if it is a bug because of the fact that it didn't work the first time then it worked once and now it isn't working again.

---

### Post by KThrace on 2008-01-23
Assuming you're not fiddling with the game settings, it seems likely that what's happening is another program is running which is taking control of the sound system in Ubuntu, and is not freeing it up for other programs (in this case, Urban Terror). Since it happens every now and then, you might have run the program which is hogging the sound but aren't aware of it, hence the random-like nature of the problem.

Make sure that no other programs like music players, video players, etc. are running in the background when you start the game. If that doesn't work, try rebooting and load up the game, see if the sound works then.

---

### Post by wormeyman on 2008-01-23
No luck doing that :(

---

### Post by wormeyman on 2008-01-25
Anyone else have any ideas?  I also have no sound in micropolis although i don't actually know if there is any...

---

### Post by steeleyuk on 2008-01-25
There is a problem with slightly older versions of Micropolis. There has been a patch which fixes that however. It might be a while before it gets packaged but you can find it [here]("http://git.zerfleddert.de/cgi-bin/gitweb.cgi/micropolis")

---

