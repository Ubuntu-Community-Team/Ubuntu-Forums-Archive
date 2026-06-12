---
title: "Application to see all shares."
date: 2011-10-28
forum: Desktop Environments
---

### Post by Azyx on 2011-10-28
It there any application who list all types of shares (samba, sshfs, web, nfs, ftp), in 10.04LTS and 11.04 and 11.10? Should also be nice to list not working shares.

/Cheers

---

### Post by crdlb on 2011-10-28
Do you mean as the client or the server? If client, are you only concerned with gvfs mounts ('Connect to Server' in nautilus) or others as well?

---

### Post by Azyx on 2011-10-28
> **crdlb said:**
> Do you mean as the client or the server? If client, are you only concerned with gvfs mounts ('Connect to Server' in nautilus) or others as well?

No I mean shared folders on the server. For a couple of years ago Ubuntu had something called 'shares' or someting under system menue. You may also get some information with:

```
net usershare info --long
```

but there are not shares you made by edit smb.conf

---

