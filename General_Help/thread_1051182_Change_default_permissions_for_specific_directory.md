---
title: "Change default permissions for specific directory?"
date: 2009-01-26
forum: General Help
---

### Post by jadoti on 2009-01-26
On my box, I created a directory (/media/disk/Shared), and a group (share).  The directory is owned by me and the group, with 775 as the permissions on the directory.

I added a user to my system (user2) and created a soft link in his home folder to this Shared directory.  I added user2 to the share group, and now he can upload and download files from that Shared directory (this is all setup to share a directory over sftp)

My question is, after user2 uploads a file, the ownership/permissions on the file are user2:user2 and 755.

I'm wondering how I can set, for this Shared directory only, a umask of sorts that will make files added there owned by {user}:share (the group) and 775 as the permissions.

Can anyone point me in the right direction?  I don't want to set umask for the user, that seems to apply to the user's creation of files anywhere on the system.  I want these files to be set like this only in this directory.

Thanks,
Mike

---

### Post by ajcham on 2009-01-26
I can't provide a direct solution as asked, but if nothing else is forecoming perhaps a cron script which periodically runs the following would be an acceptable workaround?:
```
chown -R :share /media/disk/Shared
chmod -R 775 /media/disk/Shared
```

Even if this is no good, at least I've bumped the thread for you. ;)

---

### Post by jadoti on 2009-01-28
lol!  Well, I hope there's a better solution out there, but thanks for the suggestion and the bump anyways ;)

---

### Post by abrahamsmith on 2009-02-18
You need ACL's:
```
setfacl -m default:group:groupname:rwx dirname
```

---

