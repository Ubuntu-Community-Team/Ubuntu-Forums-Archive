---
title: "I/O error when attempting to modify writable samba share mounted with CIFS"
date: 2009-01-11
forum: General Help
---

### Post by malathion on 2009-01-11
**Background**

I have a "closet fileserver" running Ubuntu 8.04 that I use to share my media (music, movies) and to run rtorrent and vsftpd. (*ryan-files*)

Here is the smb.conf from ryan-files: [http://paste.ubuntu.com/103651/](http://paste.ubuntu.com/103651/)

My main desktop system (*ryan-desktop*) runs Ubuntu 8.10 amd64. From this machine I can administer the fileserver via ssh, and I can browse (and modify!) the shared folders using samba in nautilus by entering smb://<IPADDY>/ in the address bar. I do not get any errors with reading and writing files to my shares in this way.

However, some applications I need to use (such as foobar2000 music player that I run in wine) do not like to play music and videos this way, so I mounted the remote shares with fstab. 

Here is the fstab file from ryan-desktop: [http://paste.ubuntu.com/103652/](http://paste.ubuntu.com/103652/)



**Problem**

When I try to access /media/public on ryan-desktop, which is the mountpoint for the remote shares, I can read and access files just fine. However, if I try to write to the shares (by creating, renaming, deleting, or changing permissions) I get errors. For example, when creating a file the error is "Error opening file '/media/public/upload/new file': Permission denied". When deleting a file, the error is "Error removing file: Input/output error".

This is quite frustrating and strange, since I can write to the shares through samba in nautilus, but not through the mountpoint.

When the mountpoint is mounted, these are its permissions:

```
drwxrw-r-x  7 ryan 0 2009-01-06 20:54 public/
```

Any ideas what is going on here?

---

### Post by malathion on 2009-01-12
Bump

---

### Post by malathion on 2009-01-14
Bump

---

