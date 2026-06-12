---
title: "how to force new file permissions in directory?"
date: 2009-06-07
forum: General Help
---

### Post by bertmanphx on 2009-06-07
Hello,
I've setup an NFS server with 9.04.  The clients have access to the NFS mount and can write and read to the directory.
I need to configure this directory such that any new files made, or moved there are rw by all users.
I have all users set to have "users" as their default group, and changed the rwx permission on this directory so that it's all rwx to everyone.

Whenever I create a new file from user 1, user 2 can access, but cannot write to it.  user 1 has to manually change the permissions of this file for user 2.

I have tried changing the acl's on the directory, but it said the operation was not permitted.

Also, I have read about umask, but it appears that changing this default setting, may not help in all cases.

Surely, there is some way to FORCE the permission of all new files to be RW by all?

Thanks,

bertmanphx

---

### Post by DGortze380 on 2009-06-07
If all users are in the "users" group, it should be as simple as:

```

sudo chgrp users /path/to/my/NFS

```

---

### Post by bertmanphx on 2009-06-07
DGortze380,
Nope, that didn't work.  If I create a new file, it has the permissions of rw r r

I think this is the default way that Ubuntu is setup with umask as a user correct?  When a person creates a file, it is automatically rw r r.

How do I overwrite this for the directory being shared?

Thanks,

bertmanphx

---

### Post by DGortze380 on 2009-06-07
Maybe these will help?

It appears umask is not what you need, but rather a way to change the default permissions for Nautilus/Gnome and a umask.

[http://ubuntuforums.org/showthread.php?t=40617](http://ubuntuforums.org/showthread.php?t=40617)
[http://tombuntu.com/index.php/2008/05/30/enable-the-advanced-file-permissions-dialog-in-nautilus/](http://tombuntu.com/index.php/2008/05/30/enable-the-advanced-file-permissions-dialog-in-nautilus/)

---

### Post by bertmanphx on 2009-06-07
DGortze380,
I do have the Advanced Permissions enabled, and have set the group for the directory to be 'users'.  All files created do have the group 'users', but still have no rw permissions for anyone other than the owner of the file.

I could change the behavior of Nautilus when creating new files, but I'm not sure this should be a "global change".

bertmanphx

---

### Post by bertmanphx on 2009-11-15
I did figure out how to do this, with the help of the Ubuntuforums.  See the end of these [posts]("http://ubuntuforums.org/showthread.php?t=738099&highlight=pam_umask") here.

bertmanphx

---

