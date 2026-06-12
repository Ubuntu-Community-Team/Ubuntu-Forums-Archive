---
title: "Ubuntu 9.04 Fresh Install / Open Office Read Only Problem"
date: 2009-06-04
forum: General Help
---

### Post by aussiedaddy on 2009-06-04
Hi all

I have a rather strange problem.  I did some fresh installs of Ubuntu 9.04 on PCs and set them up to have an NFS4 share from our Linux server.  That all worked fine however and I can save files to them from OpenOffice 3.0.1 Build 9379.  However if I close a file and try to re-open it it opens in read only mode.  I spent hours checking and rechecking that NFS was configured correctly (user IDs and group IDs are all set the same, /etc/fstab and /etc/idmapd.conf matches etc.)  I can't find anything wrong.  Plus gedit can happily save a file to the same location and re-open it in read-write mode. However, to make things even more confusing the problem doesn't occur if you save a file to the local drive o0n these PCs and it doesn't ever occur on another PC that I upgraded to 9.04. My best guess is that maybe there is some configuration parameter, perhaps in Open Office that defaults differently for a fresh install and is somehow causing problems with NFS?  This problem is starting to have a significant negative impact on our productivity and is very frustrating.  I would be most grateful for any help others may be able to provide.

Thanks

---

