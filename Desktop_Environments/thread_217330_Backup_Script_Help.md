---
title: "Backup Script Help"
date: 2006-07-17
forum: Desktop Environments
---

### Post by amunimanghi on 2006-07-17
Hi,

I want to backup my website files daily so I created a backup script:
```
#! /bin/bash
mv /home/ameen/html /media/storage/
```

This moves the entire folder though. Should I use ***cp*** instead?
One more thing, can I make so it executes this hourly on its own? Thanks.

~Amunimanghi

---

### Post by bruenig on 2006-07-17
probably want to use cp

---

### Post by amunimanghi on 2006-07-17
Ok, I have cron installed but how do I run it? I typed it in the consol and got this: ```

ameen@manghi:~$ sudo cron
Password:
cron: can't lock /var/run/crond.pid, otherpid may be 4726: Resource temporarily unavailable
ameen@manghi:~$
```

EDIT: I ran the script and I got this.

```
ameen@manghi:~/Desktop$ sh backup.sh
cp: omitting directory `/home/ameen/html'
``` What does this mean and how do I fix it?

---

### Post by aysiu on 2006-07-17
I would use *rsync*: ```
#!/bin/bash
rsync -av /home/ameen/html /media/storage
``` It has the advantage of copying only the files that have been changed or added since the last time you copied.

P.S. Works only if /media/storage is a Linux filesystem and **not** FAT32 or FAT16.

---

### Post by amunimanghi on 2006-07-17
Thank you very much aysiu, it worked like a charm.

---

