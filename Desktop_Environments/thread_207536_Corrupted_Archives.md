---
title: "Corrupted Archives"
date: 2006-07-02
forum: Desktop Environments
---

### Post by dfego on 2006-07-02
This isn't a support question in the sense that something broke, as much as I broke something and was hoping someone could help me fix it.  I was in the middle of using Xarchiver to do some operations on a large .tar.gz file, and I KILLed it in the middle of it (don't ask me why).  Now I can't touch the archive with a 10-foot pole.  I can't get anything out of it, even when I try to extract individual portions.  Does anyone know of anything I can do?  I'm willing to accept that some portions of the archive are gone forever, but some portions I can still see when I try to do operations, so I know (or think) they're still there...

---

### Post by dfego on 2006-07-02
I solved my problem.  Just for anyone who might have this problem themselves, here's the solution: --ignore-failed-read.  So:

$ tar --ignore-falied-read -xzvf htdocs.tar.gz

---

