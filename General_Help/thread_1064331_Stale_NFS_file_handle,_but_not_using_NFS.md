---
title: "Stale NFS file handle, but not using NFS"
date: 2009-02-08
forum: General Help
---

### Post by Gorgapor on 2009-02-08
I have a file that i cannot access or delete, and it gives the error message "Stale NFS file handle". I am not using NFS, and I am accessing the drive through a Live CD. Rebooting and unmounting/remounting don't work.

---

### Post by Gorgapor on 2009-02-08
Fixed. I used the advice from this post: [http://ubuntuforums.org/showthread.php?t=1060847&highlight=stale+nfs+file+handle](http://ubuntuforums.org/showthread.php?t=1060847&highlight=stale+nfs+file+handle)

I booted into a livecd, ran gparted, and partition -> check. That ran e2fsck, which removed the offending file.

Just for posterity, the file was /etc/resolv.conf, which is really important for DNS. So I was without any DNS resolution at all. However, there was a file /etc/resolv.conf.tmp, which seemed to have the right contents, but I couldn't rename it to the real path without fixing this nfs issue first.

---

