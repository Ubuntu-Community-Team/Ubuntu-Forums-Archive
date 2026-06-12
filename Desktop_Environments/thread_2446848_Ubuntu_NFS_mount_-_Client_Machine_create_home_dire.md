---
title: "Ubuntu NFS mount - Client Machine create home directory?"
date: 2020-07-07
forum: Desktop Environments
---

### Post by tkwok on 2020-07-07
So I am using fstab and NFS mount with SSSD to authenticate through a Windows Active Directory Server and noticed that if I log in to my accounts using the NFS server I am able to create the home directories that the client machines can access...

But is there a way to log in to the client machines using SSSD and create the home directories? I believe that the NFS server does not allow the client machines to write on the central mount point, so they are unable to create their own folder in the first login. Is there a way to get around this?

---

