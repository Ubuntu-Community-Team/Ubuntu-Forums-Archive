---
title: "Raid over NFS Shares?"
date: 2009-01-27
forum: General Help
---

### Post by FLeiXiuS on 2009-01-27
So let's hear how possible this might be.  Is it possible to use mdadm with nfs multiple NFS drives?  Rather using physical hard disks I would like to use NFS shares for raid.

---

### Post by jerome1232 on 2009-01-27
Wouldn't you want to just implemnt a RAID array on the server that's hosting the nfs shares?

---

### Post by FLeiXiuS on 2009-01-28
No, there will be multiple shares over several servers.  There will be one server where all of the shares are then mounted.

---

### Post by samborambo on 2009-01-28
Yes, this is possible but not with NFS. This is a form of storage clustering but you'd get much better performance on a single host.

Use network block devices, nbd. Do some googling on network block devices in linux.

Don't ever put swap on an NBD.

---

### Post by mb_webguy on 2009-01-28
A partition mirrored across multiple servers?  Sounds like a server farm to me.  I don't know how well it can be limited to a single partition rather than whole systems, but it's not a new idea.  This is how the big web sites like Google or Amazon can handle millions of requests at a time -- when you connect to their servers, you're actually connecting to one of numerous identical servers.  Data and services are mirrored across the entire server farm to handle a greater load.

---

