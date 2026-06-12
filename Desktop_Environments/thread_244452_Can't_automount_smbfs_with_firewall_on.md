---
title: "Can't automount smbfs with firewall on"
date: 2006-08-26
forum: Desktop Environments
---

### Post by veraction on 2006-08-26
I can't mount my samba share using the servername -- e.g., //mybox/homes -- but I can do it via ip -- e.g., //192.168.0.4/homes.

My firewall is set to block everything except 137-139, 445, 53, 135.

If I disable the firewall completely, it allows me to mount via servername. 

**What firewall settings do I need to modify to allow me to mount via servername?**

The error for mounting with servername and firewall enabled is 
```

$sudo mount -a
5196: Connection to mybox failed
SMB connection failed

```

[edit] I think it has something to do with resolving the IP based on the servername. If I mount it via servername with the firewall disabled, then unmount it, then mount again with the firewall enabled, it works. I think this is because of caching somewhere. (Doesn't work w/ firewall on after a restart)

---

### Post by meng on 2006-08-26
Have you edited your /etc/hosts ? This is a simple solution if your IP's never change.

---

### Post by veraction on 2006-08-26
Ok, that works. But isn't it a workaround -- just like using the ip directly in /etc/fstab -- rather than the normal way of operation?

[edit] it works == me adding "192.168.0.4 mybox" to the file

---

### Post by funchords on 2006-08-27
Is your firewall blocking queries/responses to 192.168.0.255?

---

