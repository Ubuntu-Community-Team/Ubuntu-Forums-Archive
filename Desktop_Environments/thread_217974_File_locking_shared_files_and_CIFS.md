---
title: "File locking shared files and CIFS"
date: 2006-07-17
forum: Desktop Environments
---

### Post by dgermann on 2006-07-17
Hi--

Have just set up a smb/cifs file server under Ubuntu 6.06. The Windows and Linux workstations seem to respect the file locks when the others have a file open.

Except, that is, for the file server itself. Others can open files the server has open, and the server can open files the others have open.

Perhaps that is because that system has those files mounted outside the cifs system.

Is there a solution that will lock all parties out when one user has the file open?

One thought I had: edit /etc/fstab on the server to specifically mount these shared directories as cifs, like we do on the workstations, thus:

```
//samba1/etc    /sam/etc        cifs    rw,credentials=/root/.smbcredentials
0       0
```

But I wonder if this is mounting the same files twice, and if it might trash the system if I did it.

Any ideas how to get file locking here?

Thanks!

---

