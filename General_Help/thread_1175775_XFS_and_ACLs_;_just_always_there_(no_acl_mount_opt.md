---
title: "XFS and ACLs ; just always there? (no acl mount option)"
date: 2009-06-01
forum: General Help
---

### Post by Pseudonomous on 2009-06-01
Hi Everybody,

This isn't a problem, just a curiosity:

I've been playing around with ACLs on one of my partitions, formatted as XFS, now if I specify this in fstab:

```
UUID=c805f435-26c2-4d63-84b6-57fc49e90c94 /storage  xfs noatime,acl 0 2
```

I can't mount it; (from dmesg)
```

[  220.200585] XFS: unknown mount option [acl].
``` 

Interesting, so I take a look at the mount man page and find there is indeed not "acl" option for XFS.  But XFS, a quick google search discovers, certainly supports ACLs.

And in fact, it looks like files/directories on the XFS *are* will hold acl data (I can setfacl / getfacl and it seems like the acls take effect as well), so are the ACL features of XFS just *always* on?  Is this Ubuntu and/or Debian and/or Linux specific behavior or does it go back all the way to Irix?

Just wondering...

---

