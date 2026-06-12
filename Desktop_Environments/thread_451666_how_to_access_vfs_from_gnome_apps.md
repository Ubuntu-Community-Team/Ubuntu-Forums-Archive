---
title: "how to access vfs from gnome apps?"
date: 2007-05-22
forum: Desktop Environments
---

### Post by nagylzs on 2007-05-22
Hi All,

I mounted some samba  volumes using the 'Places/Connect to server' menu. I guess it is integrated into nautilus, because I can copy/move files between different file systems, even if they are on different computers.  However, I'm not able to use these 'virtual' filesystems from other programs like 'pgadmin'. I understand that it would be difficult to 'mount' a folder through ssh. But why it is not possible to do with samba volumes? I noticed that the samba volumes are not really mounted with 'mount' (e.g. I tried to execute 'df' and it seems they are not mounted in the unix vfs).

Despite that, when I right click on the connection, I see "umount volume". What is happening here?

Question: how can I permanently mount these samba volumes so they can be accessed from normal applications, like pgadmin or totem?

Thanks,

  Leslie

---

