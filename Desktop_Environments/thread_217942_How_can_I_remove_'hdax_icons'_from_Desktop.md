---
title: "How can I remove 'hdax icons' from Desktop"
date: 2006-07-17
forum: Desktop Environments
---

### Post by Matodo on 2006-07-17
Hello

I am using Ubuntu 6.06, and I can't delete hda1, hda6, ... [COLOR="Red"]icons[/COLOR] from Desktop.
What should I do to remove them ?

Thanks

---

### Post by nicbink on 2006-07-17
in terminal

```
gconf-editor
```

browse to apps -> nautilus -> desktop

uncheck volumes_visible

---

### Post by Matodo on 2006-07-25
Thanks a lot nicbink
How can I make it default for all the users ?

---

### Post by aysiu on 2006-07-25
> **Matodo said:**
> Thanks a lot nicbink
How can I make it default for all the users ?
Mount them outside of the /media or /mnt directories.

For example, if you have /dev/hda1 mounted at /media/hda1, mount it at /hda1 instead.

---

