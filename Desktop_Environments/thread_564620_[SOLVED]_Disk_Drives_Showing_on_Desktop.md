---
title: "[SOLVED] Disk Drives Showing on Desktop"
date: 2007-10-01
forum: Desktop Environments
---

### Post by ashkev on 2007-10-01
I am running Edubuntu Server with 10 thin clients.  I recently created new accounts, and now all drives (floppy, hard drives, etc.) are showing on the desktop.  I know there must be a simple setting somewhere for me to have these not show, but I don't know where it is.

Thanks

---

### Post by corney91 on 2007-10-01
In gConf-Editor, go to /apps/nautilus/desktop, and untick 'Show Volumes'. That's what it is in Ubuntu, I think it'll be the same in Edubuntu.
Hope this helps.

---

### Post by meindian523 on 2007-10-01
gconf-editor can be opened by entering in terminal```


gconf-editor
```

No sudo required.....:)

---

### Post by ashkev on 2007-10-01
Thanks!

---

### Post by meindian523 on 2007-10-01
Please mark thread as solved.

---

