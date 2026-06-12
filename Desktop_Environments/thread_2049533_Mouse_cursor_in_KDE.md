---
title: "Mouse cursor in KDE"
date: 2012-08-28
forum: Desktop Environments
---

### Post by riverwillow on 2012-08-28
In my Ubuntu 12 32 bit system, the mouse cursor in KDE disappears after cursor motion has stopped for a few seconds. Is there to stop this?

Thanks,
Larry

---

### Post by ruicovelo on 2012-08-29
Do you have unclutter installed?

> $ apt-cache search unclutter
(...)
unclutter - hides the mouse cursor in X after a period of inactivity
(...)


[http://ubuntuforums.org/showthread.php?t=1547206&highlight=mouse+cursor+disappears](http://ubuntuforums.org/showthread.php?t=1547206&highlight=mouse+cursor+disappears)

---

### Post by riverwillow on 2012-08-29
Yes, I do. I looked at the man page and tried -jitter 10. That did it. Thank you very much.

---

