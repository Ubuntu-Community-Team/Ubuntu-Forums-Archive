---
title: "Mounting NAS drive so programs can see it?"
date: 2009-03-24
forum: General Help
---

### Post by the_nite_owl on 2009-03-24
I have setup a DLink NAS box to store all our files onto and it is working fine from Ubuntu, OSX and Windows boxes.
I just installed LinuxDC++ and wanted to share out some files from the NAS box but it does not seem to see network resources.

Is there a way to mount the network drive in Ubuntu that will let it appear available to local applications?

Thanks.

---

### Post by igor. on 2009-03-24
Mounting in gnome is handled by gvfs (gnome virtual filesystem). You can access these mounts through /home/username/.gvfs/protocol+user+servername/. Note that the .gvfs is a hidden folder, as its name begins with a dot.

---

### Post by the_nite_owl on 2009-03-24
> **igor. said:**
> Mounting in gnome is handled by gvfs (gnome virtual filesystem). You can access these mounts through /home/username/.gvfs/protocol+user+servername/. Note that the .gvfs is a hidden folder, as its name begins with a dot.

I can see the .gvfs folder.  How would I mount a network drive so that it would show there and make it so that it automatically mounts at boot?
Currently I access the box from the file browser with the address of smb://192.168.1.124/volume_1/

---

### Post by igor. on 2009-03-25
In this case you need to mount the drive not through gvfs, but using fstab. /etc/fstab is the file that contains all file systems that are mounted on startup. The file system you want to mount is a samba share (aka smb, windows file share).

Here's an article that will help you: [http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/](http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/)

---

### Post by the_nite_owl on 2009-03-29
> **igor. said:**
> In this case you need to mount the drive not through gvfs, but using fstab. /etc/fstab is the file that contains all file systems that are mounted on startup. The file system you want to mount is a samba share (aka smb, windows file share).

Here's an article that will help you: [http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/](http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/)

That did the trick.
I had tried setting the fstab line first which did not work.  Had to mount the drive first then the entry in fstab worked.

---

