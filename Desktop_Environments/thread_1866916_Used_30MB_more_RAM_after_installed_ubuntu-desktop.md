---
title: "Used 30MB more RAM after installed ubuntu-desktop"
date: 2011-10-22
forum: Desktop Environments
---

### Post by elliotlo on 2011-10-22
Is it normal?

In addition to change the grub file, is there another way that I can 'ask' to system to boot to console? (boot to Desktop whenever it is needed only)

Thanks for your idea.

---

### Post by ajgreeny on 2011-10-22
You can edit the line in /etc/default/grub that reads ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` and add the word text so it reads
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"
```
You will then get a cli desktop, and can start an xsession when you need with ```
startx
```

---

