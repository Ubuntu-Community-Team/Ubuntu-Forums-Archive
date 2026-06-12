---
title: "User Authorizations - mounting remote shares"
date: 2009-03-06
forum: General Help
---

### Post by crokett on 2009-03-06
I have a shell script that mounts some Samba shares, runs an rsync from the share to a local folder then unmounts the share.  The mount promts for a sudo password. I don't want it to.  It is annoying when run from the command line. I also want to schedule my script. I made what I thought is the correct entry in visudo but it still prompts for a password.  Here is the entry I made.  

```

 greendm   ALL=(ALL) /bin/mount,/bin/umount,/sbin/mount.cifs,/sbin/umount.cifs

```

I also set authorizations for mounting filesystems via the GUI tool under System->Administration but that did not work either.

---

### Post by beno1990 on 2009-03-06
Try replacing ALL=(ALL) with ALL = NOPASSWD:

---

### Post by crokett on 2009-03-06
That worked.  Thanks.

---

