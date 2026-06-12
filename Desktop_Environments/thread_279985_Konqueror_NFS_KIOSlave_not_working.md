---
title: "Konqueror NFS KIOSlave not working"
date: 2006-10-18
forum: Desktop Environments
---

### Post by ERam123 on 2006-10-18
I have 2 machines: a desktop and a laptop.

I have NFS shares set up onthe desktop and I am able to successfully mount them from command line and access them from command line and from within Konqueror.

When I try to access the shares with the NFS KIOSlave (via nfs://server/share) it doesn't work.  All I get is the error

```
Authorization failed , [server name] authorization not supported
```

Has anyone else experienced this or does anyone know why this might be happening?

---

### Post by ERam123 on 2006-10-18
Found the solution to my own problem.

When sharing a folder via NFS, you must add insecure to the exports entry if you want to browse it with konqueror's kioslave...

```
/home/erik/blah *(async)
```

becomes

```
/home/erik/blah *(async,insecure)
```

(these lines are in /etc/exports)

---

### Post by sanicki on 2007-06-05
Can anyone get me a little further on this?

I have a Dapper Ubuntu server sharing a folder via NFS with the async and insecure options in /etc/exports, but am unable to browse to it using either nfs:/ or nfs://<server ip>/<share path> using Konqueror on Kubuntu Feisty on the same network.

---

