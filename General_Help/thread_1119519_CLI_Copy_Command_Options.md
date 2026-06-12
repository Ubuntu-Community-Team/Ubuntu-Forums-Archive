---
title: "CLI Copy Command Options"
date: 2009-04-08
forum: General Help
---

### Post by deanjm1963 on 2009-04-08
I'm planning on doing a full 1-to-1 backup of my data to a removable.

I've been using "cp -r -v /partition/* /media/disk/partition/ up until now.

My question is ... is there an option to omit a certain folder or file while retaining the -r option or an equivalent?

e.g. I want to copy folders, folder-a, folder-b, folder-d, but not folder-c

TIA

---

### Post by amac777 on 2009-04-08
Instead of using the cp command, you can use rsync. Rysnc allows excluding directories and files.

For example, if you don't want the directory /partition/exclude_me to be copied, try this:

```
rsync -av --exclude='/partition/exclude_me' /partition /media/disk
```

Note: the -av command means to archive recursively while keeping all the attributes (time, date, permissions) of the files the same, and the v part means to show verbose information of each file as it is copied.

For more info you can look at the examples in the rsync man page or on this web page:

[http://articles.slicehost.com/2007/10/10/rsync-exclude-files-and-folders](http://articles.slicehost.com/2007/10/10/rsync-exclude-files-and-folders)

---

### Post by deanjm1963 on 2009-04-08
> **amac777 said:**
> Instead of using the cp command, you can use rsync. Rysnc allows excluding directories and files.

For example, if you don't want the directory /partition/exclude_me to be copied, try this:

```
rsync -av --exclude='/partition/exclude_me' /partition /media/disk
```

Note: the -av command means to archive recursively while keeping all the attributes (time, date, permissions) of the files the same, and the v part means to show verbose information of each file as it is copied.

For more info you can look at the examples in the rsync man page or on this web page:

[http://articles.slicehost.com/2007/10/10/rsync-exclude-files-and-folders](http://articles.slicehost.com/2007/10/10/rsync-exclude-files-and-folders)

Thanks heaps for that... solved my problem.

---

