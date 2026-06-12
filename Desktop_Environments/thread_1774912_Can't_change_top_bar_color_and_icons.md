---
title: "Can't change top bar color and icons"
date: 2011-06-03
forum: Desktop Environments
---

### Post by mothergoose729 on 2011-06-03
Just installed Ubuntu 11.04 where by default the top bar, where the ubuntu log and the time hangs out, is this nice dark humanity theme that fits in wonderfully with ambiance. I am not all sure what happened... as far as I know all I did was update the system and now the top has much more of a kde/clear looks theme too it. I want the old look back. I looked through the appearance app and cssm and couldn't seem to find the settings I need. What do I need to do to change it back?

[s]Also, as a completely unrelated question, I would love it if I could change the order of the apps in the unity bar in addition to which apps have icons there. If anyone knows how to do that please let me know.[/s] 

Thanks for any help, and may you be graced with many beans.

---

### Post by mothergoose729 on 2011-06-04
Didin't know it, but this was the cause of a gnome daemon snafu. Looked in another thread and this code sequence helped me.

```
killall gnome-settings-daemon
gnome-settings-daemon
```

Thank you ubuntu forums :).

---

