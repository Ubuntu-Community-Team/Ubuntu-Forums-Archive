---
title: "Maxtor 1TB USB drive not automounting"
date: 2009-11-01
forum: Desktop Environments
---

### Post by duncan_bayne on 2009-11-01
Hi All,

I fear I must be missing something straightforward here, & would appreciate any advice.  I have a Maxtor 1TB USB drive that I'd like to automount on startup.  I have created a corresponding entry in /etc/fstab:

```
/dev/sdb1   /media/disk  ntfs-3g  defaults  0  0
```

This doesn't work; the drive is not mounted at boot.  However if I open a terminal and enter:

```
sudo mount /media/disk
```

... then the drive mounts read-write, just as I hoped it would.  So I'm stumped.  I can't work out why it's happy to mount manually, but not automatically.  

TIA for any suggestions ...

---

### Post by celtic426 on 2009-11-01
Not sure if this will help in your case, but what I did to automount my external drives was download ntfs-3g (it's in the repositories) and set it to mount drives automatically by just opening it and clicking a check box.

---

### Post by duncan_bayne on 2009-11-01
> **celtic426 said:**
> Not sure if this will help in your case, but what I did to automount my external drives was download ntfs-3g (it's in the repositories) and set it to mount drives automatically by just opening it and clicking a check box.

Thanks - I tried using ntfs-config, but it couldn't even *find* /dev/sdb1.

---

