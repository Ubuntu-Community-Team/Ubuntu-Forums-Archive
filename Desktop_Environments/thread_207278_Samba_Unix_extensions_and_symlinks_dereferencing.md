---
title: "Samba: Unix extensions and symlinks dereferencing"
date: 2006-07-01
forum: Desktop Environments
---

### Post by karih on 2006-07-01
Hi,

I have a fileserver at home that I access using Samba.  On the server I have the following folders
/home/kari - my home directory
/home/share - a directory shared between users of the server

Inside my home directory I have a simple symlink, called "share" that links to the /home/share.

The problem is that when I mount my remote home directory with cifs the share symlinks remains a symlink and points to a directory on my local machine, instead of the /home/share folder on the fileserver.

After searching google for a while I found out this could be "fixed" with setting "unix extensions = no" in smb.conf but then I can't see any file privileges on the server and the filesystem becomes a simple one-user, one-privileges, win-like behaviour.

**So, is there any way to dereference symbolic links on a samba server without disabling unix extensions?**

Thanks in advance!

---

### Post by jamessnell on 2008-04-01
I have this same issue. I'll post if I find a solution.

---

