---
title: "How important is AIGLX w/ NVIDIA?"
date: 2007-10-10
forum: Desktop Effects &amp; Customization
---

### Post by mjwood0 on 2007-10-10
I followed at least three or four sets of instructions here and finally have a really nice Compiz Fusion desktop going on!  But during this time, I found a [thread]("http://ubuntuforums.org/showthread.php?t=537836") which attempted to debug problems.

One of the checks was to run the following to check for AIGLX:
```
grep AIGLX /var/log/Xorg.*.log
```

Doing so on my system results in no output.

My specifications are as follows:
NVIDIA GeForce 7050 onboard video allocating 256 MB RAM.

I'm running Feisty and the latest Compiz Fusion i could find.  Compiz seems fine, but perhaps a bit sluggish -- expected since I'm running on the integrated video I would guess.

Is getting the AIGLX working really that important?  I've tried every suggestion I can find and still nothing.  I guess at this point, I really don't see the point in worrying since it's all working nicely together.  

Looking for some confirmation or suggestions I guess.

Thanks in advance!

---

### Post by Forlong on 2007-10-10
You do not need AIGLX with Nvidia at all.
It's only for intel and ATI (open radeon driver) users.

---

### Post by mjwood0 on 2007-10-10
Then the guide I quoted above is incorrect!  That makes me feel much better.  I was really stumped!

---

