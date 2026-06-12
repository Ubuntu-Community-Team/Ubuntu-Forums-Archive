---
title: "Workgrouping within Ubuntu"
date: 2005-12-21
forum: Desktop Environments
---

### Post by GQed76 on 2005-12-21
I now have 2 happy ubuntu machines.  I need to move files off a Hard drive on one over to the other over the network.

I JUST got the network cards working, so I havent had much time to play around.   Can somone direct me to a Wiki, walk through or other information

---

### Post by neurosis on 2005-12-21
You might want to look up setting up NFS or Samba to share files between the two machines.

At home one of my machines acts as an NFS server, which has a directory "/share", which my other machine (NFS Client) can mount so it appears just like any other directory.

Samba is similar, except you can view Samba shares from Windows machines, and it can share more than just files (ie: printers, etc).

I would say NFS is a bit easier to set up (albeit, less secure, I'm told - but if you're not exposing it to the internet you should be fine), but others may have different experiences.

That should be enough information for you to start your search!

---

### Post by GQed76 on 2005-12-21
Samba seems a bit much.  Ive elimated windows entirely.

I just need to get 2 ubuntu machines to share files

---

