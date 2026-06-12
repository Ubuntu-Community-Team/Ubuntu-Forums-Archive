---
title: "Is there any problem with this command(rsync)?"
date: 2009-06-13
forum: General Help
---

### Post by colau on 2009-06-13
Hi,
Is there any problem with this rsync command?
Or anything I should add or change?
I followed [this]("http://www.mikerubel.org/computers/rsync_snapshots/index.html#Incremental")
```

rsync -avpoglr --delete --delete-excluded --exclude-from=./excludes / /media/disk/backup/rsync.0

```
excludes file:
```

/proc
/sys
/dev
/tmp
/var/tmp
/lost+found
/media
/mnt

```

---

### Post by colau on 2009-06-13
Bump.
Should I add any option?

---

### Post by mannih2001 on 2009-06-13
It would really help if you told us what you are trying to accomplish. Is there any reason for suspecting that the command might not work? Did you try it? Does it give you any errors?

---

### Post by colau on 2009-06-13
> **mannih2001 said:**
> It would really help if you told us what you are trying to accomplish. Is there any reason for suspecting that the command might not work? Did you try it? Does it give you any errors?
It is still running.
I am afraid it's compression method may be poor.
I run this command to backup a 10GB partition.
But the backed up file is already 4GB and the command is still running.
It seems it is just copying the directory,no compression.
Is there any way to compress the 10GB partition into 3.5GB or around 4GB?

Thanks.

---

### Post by mannih2001 on 2009-06-13
As far as I know rsync doesn't have any kind of compression.

---

