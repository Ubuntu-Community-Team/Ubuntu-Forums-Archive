---
title: "Change Apache's root location to a NAS array on the network???"
date: 2009-01-25
forum: General Help
---

### Post by Presto-X on 2009-01-25
Hello everyone,

I'm new to ubuntu, I just got ubuntu server with LAMP installed on my dell poweredge system very easy/smooth install.

What I need to do is set apache's root web folder to a NAS drive array on my network, but I was not sure how to go about this, do I need to setup a connection within ubuntu first then edit apache's config file to look to this location?

What is the best way to go about this?

---

### Post by Alterax on 2009-01-25
> **Presto-X said:**
> Hello everyone,

I'm new to ubuntu, I just got ubuntu server with LAMP installed on my dell poweredge system very easy/smooth install.

What I need to do is set apache's root web folder to a NAS drive array on my network, but I was not sure how to go about this, do I need to setup a connection within ubuntu first then edit apache's config file to look to this location?

What is the best way to go about this?

Well, what I would do is mount the shared location on the NAS as /var/www on the webserver.  It (the NAS) may be capable of NFS sharing or SMB sharing.  Just look up how to mount a smb or NFS share in /etc/fstab on your ubuntu box, and mount the share to the /var/www directory.  Then, once you reboot the Ubuntu box (or issue the **sudo mount -a** command), it'll look at the share on your NAS whenever Apache gets a web request.

---

### Post by Presto-X on 2009-01-25
Thanks Alterax,

I will give that a shot today, I was not even sure where to start, this gets me pointed in the right direction.

Thanks again.

---

