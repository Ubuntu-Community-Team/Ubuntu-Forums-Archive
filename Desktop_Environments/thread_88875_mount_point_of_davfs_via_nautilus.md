---
title: "mount point of davfs via nautilus"
date: 2005-11-11
forum: Desktop Environments
---

### Post by RikoW on 2005-11-11
Dear all,

I can connect to a webdav server using the Places -> Connect to Server menu.
Natilus pops up and I can happily browse through the folder structure on the server. I can also copy files to the server (even though the copy progress window seems to get stuck). I webdav folder icon appears on the desktop.

However, I'm coming from old unix days, so use the CLI a lot. But so far, I couldn't find the mount point where the webdav server is connected to the filesystem. I like to cd to the directories and cp files in an out without the need to go through nautilus. 

Does anybody know, where to find the mount point for davfs? It's neither in /media nor /mnt.

Thanks,

                 Riko

---

### Post by Joe_lurker on 2005-11-11
They aren't mounted.  To mount the WebDAV folders you need to install davfs2 from the Universe.

-Joe

---

