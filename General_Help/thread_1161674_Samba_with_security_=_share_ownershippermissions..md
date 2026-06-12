---
title: "Samba with security = share ownership/permissions."
date: 2009-05-16
forum: General Help
---

### Post by Nixie Pixel on 2009-05-16
Hi, I've set up a file server using Samba and set my security to share, and modified the permissions on the mount point to give everyone access to read, write, execute.  The goal was to make it simple to connect and do work while you are on the network, no matter what username, and it does work correctly.

Except when I manipulate files from the server console itself.  Is there an easy way to make changes (for instance moving files from a backup to the file server) so that any directories made and files placed there while at the server console will have the same permissions?

Barring that is there a quick way to recursively chmod an entire directory tree and all the files within it?

Thanks!

---

### Post by mb_webguy on 2009-05-17
When you move files from one Linux machine to another, ownership and permissions should be preserved.  If you're moving files to and from an ntfs or FAT32 partition (such as on a Windows machine), then you're going to lose the ownership and permissions because those filesystems don't support Linux-style file permissions.

To recursively change the ownership and permissions of files and directories, use the "-R" option of the chown and chmod commands.

---

