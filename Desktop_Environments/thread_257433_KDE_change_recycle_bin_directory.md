---
title: "KDE change recycle bin directory?"
date: 2006-09-14
forum: Desktop Environments
---

### Post by danpre on 2006-09-14
Is there a way to change recycle bin directory in KDE?

I always backup whole user home directory, so I want to aviod wasting space for files in recycle bin.

I have created directory:
/home/temp

where I want to put all unnecessary files like:
trash
opera cache - already done
mozilla cache - already done

etc.

DANIeL

---

### Post by neoeden on 2006-09-14
I'm doing some research on this, I'll see if I can get back to you. Check this out though:

[http://lists.kde.org/?l=kde&m=110873688631581&w=2](http://lists.kde.org/?l=kde&m=110873688631581&w=2)

It seems that the freedesktop spec standized the location for the trash can....

---

### Post by aysiu on 2006-09-14
Have you tried this? ```
rm ~/.local/share/Trash/files
ln -s /home/temp ~/.local/share/Trash/files
```

---

