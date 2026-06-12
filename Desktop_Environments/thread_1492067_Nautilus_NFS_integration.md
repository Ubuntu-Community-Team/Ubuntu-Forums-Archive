---
title: "Nautilus NFS integration"
date: 2010-05-24
forum: Desktop Environments
---

### Post by dE_logics on 2010-05-24
Is there a gnome specific GUI way of making shares though nautilus. For e.g. I right click>properties>share and we only have the SAMBA options...not NFS.

So can we have such a thing for NFS (like we have in KDE), or is there an easy GUI which does this?

---

### Post by dE_logics on 2010-05-25
So there's no GUI way?

---

### Post by dE_logics on 2010-05-25
I cant believe this! It was there in Gnome before...:-x

---

### Post by dE_logics on 2010-05-28
Bump.

---

### Post by fackamato on 2011-03-02
Doesn't look like it. :(

---

### Post by EricDHH on 2011-05-06
BUUMP

cannot believe this, ubuntu is linux and his filemanager supports only samba.I tested other solution and ways but all are very ugly. Autofs5 did cause a lockup and failures with nautilus #762600 so this is no solution. A static mount in fstab is also an unclear solution, cause it will stay for every user and not user based.

More ideas?

---

### Post by jhansonxi on 2011-12-14
> **EricDHH said:**
> More ideas?
Possible solution to [bug #29263]("https://bugs.launchpad.net/gvfs/+bug/29263"):
**[nfs-lan]("http://nfs-lan.sevka.info")**

---

### Post by thaelim on 2011-12-16
You are correct - there is no simple way. Do yourself a favour and stay away from NFS if you can - I use it as part of my work (we built a product around it because we had no other option!) and I can tell you it's a horrible pile of bugs. Samba is very nice and stable these days, fully integrated with Nautilus etc and works perfectly.

---

### Post by sevka on 2013-03-20
Check out this: [http://nfs-lan.sevka.info/](http://nfs-lan.sevka.info/)
Github: [https://github.com/sevka/nfs-lan](https://github.com/sevka/nfs-lan)

---

### Post by TheFu on 2013-03-20
Samba is a user-oriented way of sharing. Any user can connect to a remote Samba share as they like, provided their credentials fit.

NFS is a server-to-server way of sharing. The shares are there regardless of user.  This means a user-to-server mapping needs to be extremely carefully considered before deployment, since NFS uses UIDs to determine file system access.  Any rogue computer could spoof user IDs and connect to an NFS server, effectively taking over files owned by a different persion without any real credentials - just the userid is enough.  So, to combat all this, **NFS must be setup by root on both sides of the connection.  **Older versions only used the IP address to determine whether NFS clients and servers should communicate or not.  This can be insecure, as IP addresses can be taken over.  Newer versions allow using certificate authentication, but still for root/root control.  End-users need not attempt this.

NFS is more efficient and more capable than Samba. The file system permissions are almost identical to locally mounted UNIX/Linux permissions.  Softlinks work across NFS and hardlinks work locally on the same file system, if I recall correctly, plus there are all the normal sticky bits and rwx aspects.

Anyways, hopefully, this has explained a little as to why NFS isn't part of nautilus remote mounting.
For end-user-controlled mounts, samba and sshfs are probably the best options, but I must admit I do not use any "file manager", so I may not be the best person to be commenting here.

---

### Post by oldos2er on 2013-03-20
Old thread closed.

---

