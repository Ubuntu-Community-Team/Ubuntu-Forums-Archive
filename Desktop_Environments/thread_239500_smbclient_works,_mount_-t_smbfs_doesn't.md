---
title: "smbclient works, mount -t smbfs doesn't"
date: 2006-08-19
forum: Desktop Environments
---

### Post by xp_newbie on 2006-08-19
I am trying to access Samba shares (on another Linux server) from the **command line** (xterm).

Using smbclient works without any problem:

> smbclient \\\\servername\\myshare -U myself

But attempting to mount (my preffered mode of work) simply doesn't. The following 

> mount -t smbfs //servername/myshare /mnt/servername/myshare -o user=myself

Yields an error message:

> 5484: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed.

Please note that I have ommitted the password from here, but I did enter it properly - when prompted to do so. Also, the mount point /mnt/servername/myshare exists (created manually).

Any idea how to make mount -t smbfs work?

Thanks!
Alex

---

### Post by VirtuAlex on 2006-08-19
have you tried to move -o options to a beginning of the line?

---

### Post by xtknight on 2006-08-19
Try cifs instead of smbfs.  cifs works for newer Windows servers.

---

### Post by xp_newbie on 2006-08-19
> **VirtuAlex said:**
> have you tried to move -o options to a beginning of the line?

Yes. It yields the same exact results. :(

---

### Post by VirtuAlex on 2006-08-19
by the way it is not user= it is username=

---

### Post by xp_newbie on 2006-08-19
> **VirtuAlex said:**
> by the way it is not user= it is username=

That was my problem!

Thank you very much. :)

---

