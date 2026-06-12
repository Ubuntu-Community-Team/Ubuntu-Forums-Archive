---
title: "I Need Permission"
date: 2009-06-02
forum: General Help
---

### Post by LubeckTech on 2009-06-02
I am trying to copy files from my desktop to a ext2 partition on a SD card but I keep getting an error message telling me that I don't have permission. In the permissions tab for the partition it says the partition bleongs to Root. How do I give myself permission to copy files and untar files? I am running Ubuntu with only one user account.

---

### Post by colau on 2009-06-02
> **LubeckTech said:**
> I am trying to copy files from my desktop to a ext2 partition on a SD card but I keep getting an error message telling me that I don't have permission. In the permissions tab for the partition it says the partition bleongs to Root. How do I give myself permission to copy files and untar files? I am running Ubuntu with only one user account.
```

sudo cp <filename> <wheretocopy>

```
See also
```

man cp

```
Which ubuntu version are you using?
And what's the filetype of SD card?

---

