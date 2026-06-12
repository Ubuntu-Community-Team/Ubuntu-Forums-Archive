---
title: "So where did KDE 4.2 go???"
date: 2009-02-28
forum: Desktop Environments
---

### Post by SunnyRabbiera on 2009-02-28
Alright for fun I put regular Kubuntu in a virtualbox and wanted to see if it could use kde 4.2, but one major issue:
KDE 4.2 is gone, missing, bye bye.
None of the repos I was referred to have it anymore!
I cant stand kde 4.1, KDE 4.2 is much better in my experience but there are no longer any binaries to be found!
What to get KDE 4.2 now I have to compile?

---

### Post by Monsieur Gonzalez on 2009-02-28
Hi!

If you're using 8.10, you'll find them in the backports repository.

---

### Post by yther on 2009-02-28
...except for a little, teeny, but possibly important bit called "plasma."  :(

I've told myself I'm not going to update until doing so won't break things, so I still wait....

---

### Post by Monsieur Gonzalez on 2009-02-28
I was using the PPA repository for KDE4.2 and then changed to backports and have not missed any package, everything working right here. What's the exact "plasma" package you're refering to??

---

### Post by wieman01 on 2009-02-28
I have upgraded to 4.2 and have not had any issues since. Well, if you consider the lack of sticky keyboard shortcuts an exception. Apart from this, it runs nicely and looks really great.

---

### Post by SunnyRabbiera on 2009-02-28
ah so they moved it to backports finally

---

### Post by wieman01 on 2009-02-28
Go for it, it's simple.

---

### Post by yther on 2009-02-28
> **Monsieur Gonzalez said:**
> I was using the PPA repository for KDE4.2 and then changed to backports and have not missed any package, everything working right here. What's the exact "plasma" package you're refering to??

libplasma2

Looks like I was confused by the numbering of that, however, and libplasma3 is replacing it.

**Edit:  To anyone looking to upgrade KDE who is also running the 180.35 version of NVIDIA drivers, don't.  :(  You should either regress your NVIDIA to 180.29, or stay with KDE 4.1.  I had multiple problems, such as nepomuk crashing, unable to log out properly, no session management, and was struggling with KDE stuff when I happened to stumble across some discussion on nVnews (I think) in which many people on many different distros had similar problems.  I reverted to 180.29 and (aside from Lancelot, which has its own trouble) everything works as expected.**

---

