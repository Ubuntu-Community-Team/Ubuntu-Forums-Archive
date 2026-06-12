---
title: "update install problem"
date: 2009-01-25
forum: General Help
---

### Post by tomgwyther on 2009-01-25
I can't seem to install updates, or new applications.
If I try I get this message...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

any ideas as to how I can get around this; have it installing things automatically.

Any help would be much appreciated

Thanks

---

### Post by x33a on 2009-01-25
did you try dpkg --configure -a?

try it and post the result.

---

### Post by hansdown on 2009-01-25
Hi tomgwyther.

Click applications> accessories> terminal.

Copy and paste the following.

```
sudo dpkg --configure -a
```

Hit enter. Give your password; you won't see it as you type. Hit enter and you're done.

---

### Post by Michael.Godawski on 2009-01-25
hi,

hansdown is right, do the suggested above.

This error message usually crops up when the installation process was somehow interrupted, so packages remain "broken", half-installed.

---

