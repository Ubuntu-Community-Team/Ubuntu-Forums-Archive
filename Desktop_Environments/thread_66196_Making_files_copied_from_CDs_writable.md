---
title: "Making files copied from CDs writable"
date: 2005-09-16
forum: Desktop Environments
---

### Post by ehsan on 2005-09-16
This is more of an annoyance than a problem, and is common to all GNU/Linux distros.

CDROMs are always mounted ro, and this is correct, since nothing can be changed on them.  But it causes problems when copying large sets of files and dirs from them, as all of the files and dirs have the w permission bits truend off.  If there are a few, it is easy to fix in Nautilus.  If thare are much, a 'cd /path/to/files && chmod -R u+w *' can fix it, but it gets annoying after doing it for the thousandth time...

I can't imagine there is not an easier fix for this problem.  Does anyone here know of any?

Thanks!
Ehsan

---

