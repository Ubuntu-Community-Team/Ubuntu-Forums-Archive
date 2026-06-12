---
title: "ntfs read only in server version"
date: 2008-12-28
forum: General Help
---

### Post by mr.wu on 2008-12-28
I have been using redhat/fedora line users for a long time... I have installed the latest ubuntu 8.10 both desktop and server versions.  While desktop version lets me use ntfs partition read-write, server version won't let me write to ntfs partitions.  What gives?  Also it's strange that in server edition /etc/mtab shows ntfs partition is mounted rw but I cannot write to it.  I have attempted to do remount with rw flag but that's no good.

Is it because ntfs binaries are different in desktop and server editions?

If there is no easy way around it I would like to use a stripped down version of desktop.  I cannot figure how to strip out packages I do not want from desktop version during the install.  It also does not seem easy to remove lots of packages after the install either.

---

### Post by dcstar on 2008-12-28
> **mr.wu said:**
> I have been using redhat/fedora line users for a long time... I have installed the latest ubuntu 8.10 both desktop and server versions.  While desktop version lets me use ntfs partition read-write, server version won't let me write to ntfs partitions.  What gives?  Also it's strange that in server edition /etc/mtab shows ntfs partition is mounted rw but I cannot write to it.  I have attempted to do remount with rw flag but that's no good.

Is it because ntfs binaries are different in desktop and server editions?
.......

Install the ntfs-3g package.

---

