---
title: "ext partition being mounted with different owner User"
date: 2009-01-20
forum: General Help
---

### Post by nlbs on 2009-01-20
Just Installed Kubuntu 8.10
While Installation the default user name I provided was `neel`
after playing with Plasmoyid widgets Desktop refused to start on next reboot.
I tried a lot. But It didn't work.
so I changed the username `neel` to `nlbs`, deleted already created `neel` group and created another user  called `neel` and it worked again with `neel` User.

But Now When I automount some ext partition. its owner user is still `nlbs`
and Its same on my External Hard Disk's Ext2 Partition.

User `neel` belongs to all those groups that `nlbs` used to belong to.

I removed the `nlbs` User and now
Its showing up the User Id Instead of User `neel`
```
drwxrwxrwx 22 1000 root  4096 2009-01-18 22:43 ent 
```
I think If I change UID of `neel` to `1000` It will work. Would It ??
If yes Is that a back door ??

But Why its not working ??
and Whats the real solution ??

Thanks

---

