---
title: "Conduit sync software"
date: 2011-04-08
forum: Desktop Environments
---

### Post by svenole on 2011-04-08
I've just installed Conduit 0.3.17 to synchronize an SMB catalogue to my laptop (ubuntu 10.04) and vice versa. This works fine, but I've run into an issue where I need to be able to add exeptions to the sync. The network volume (CIFS home catalogue) is on a NetApp system with snapshot enabled. The result of this is that there is a ~snapshot catalogue residing on the network top directory. This snapshot directory can not be a part of the sync process ( it destroys the sync completely because of the size and there is no point keeping this in sync locally)

Now, it seems to me that there is no way of handling exeptions in Conduit. At least I can not find it. Now I need to set up sync for every directory under the top one to get passed this issue.... Anyone out there that have solved this issue ? 

- Sven

---

