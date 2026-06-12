---
title: "Flash Player Problems"
date: 2010-10-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by klaxor on 2010-10-24
I'm attempting to update my Flash player and can't seem to figure it out.  I've downloaded the update, tried to run it, but the package manager didn't finish and said I needed to close other program managers before running it.  I closed everything else and tried again, but the same thing happened.  Restarted the computer, tried again.  Now the package manager won't open and I get this message:

"E:dpkg was interrupted, you must manually run 'dpkg --configure-a' to correct the problem.
E:cache->open() failed, please report"

I'm also running on a super-minimal computer, 4 GB hard drive.  The Dell Mini 9 wasn't my best choice of computers to learn Linux on.

Oh, Ubuntu 8.04, if you're wondering.

Any advice/commands?

---

### Post by klaxor on 2010-10-24
*twiddles thumbs*

---

### Post by MartijnV on 2010-10-25
Tried this already?

dpkg --configure-a

You might want to type the above in a terminal. I don't remember if you need to run it with sudo, but you'll find out soon enough.

About flash, I think I remember I used to use the manual installer from the adobe site when I had older versions of ubuntu?

(p.s. buy a more spacious hard drive? They aren't that expensive?)

---

