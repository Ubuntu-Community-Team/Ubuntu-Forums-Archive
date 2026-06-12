---
title: "Mount Shared Folder"
date: 2009-04-30
forum: General Help
---

### Post by uchacker11 on 2009-04-30
I am having trouble mounting a shared folder by editing fstab.  The folder is on a server running Ubuntu server shared with samba.  I entered the following line into fstab but it is giving me a "mount: wrong fs type" error.

//192.168.1.103/IT /mnt/IT smbfs users,auto,credentials=/home/.smbcredentials,uid=myusername,gid=users 0 0

any help would be appreciated, it was working just fine in 8.10 but in 9.04 it stopped working.

---

### Post by uchacker11 on 2009-04-30
nevermind I figured it out.  smbfs was not installed for after upgrade.

---

