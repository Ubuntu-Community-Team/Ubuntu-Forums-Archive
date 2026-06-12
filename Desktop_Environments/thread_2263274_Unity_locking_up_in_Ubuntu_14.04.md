---
title: "Unity locking up in Ubuntu 14.04"
date: 2015-01-30
forum: Desktop Environments
---

### Post by skilo47 on 2015-01-30
I have been using 14.04 for about a day now and everything was going fine until i rebooted and now unity locks up every now and then, Somtimes it refuses to even start the GUI but i can f1 into the shell after a few minutes.

After i got to the shell i noticed this error message:

```
"[  141.925753] [drm[:i95_set_reset_status] *ERROR* render ring hung insdie bo (0x1bff000 ctx 0) at 0x1bff2d4"
```

Not sure what the problem could be.

---

### Post by mooreted on 2015-02-01
Check the following thread and see if changing the acceleration method to UXA helps:

[http://ubuntuforums.org/showthread.php?t=2208072](http://ubuntuforums.org/showthread.php?t=2208072)

---

