---
title: "No sound in flash"
date: 2006-08-24
forum: Desktop Environments
---

### Post by music_man on 2006-08-24
Hi

I have tried to get flash to work in Firefox and it works but no sound is played. I downloaded flash and copied a file into the firefox folder (as far as I can remember), am I supposed to copy anything else?

Thanks

---

### Post by Jagot on 2006-08-24
Try this:

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd 
```

---

### Post by music_man on 2006-08-24
It worked!

Thanks!

---

### Post by iblis on 2006-08-29
the symlink seems to have fixed it for me,  as well.

anyone know what caused it in the first place? i had sound working just fine in breezy...

thanks!

---

