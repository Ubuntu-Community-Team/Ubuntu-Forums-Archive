---
title: "vfat mount options - gid parameter invalid?"
date: 2009-01-14
forum: General Help
---

### Post by ByteDoc on 2009-01-14
Hello there,
I recently discovered the default mount options via the Gconf Configuration Editor - I want to mount my USB sticks and SD cards with certain permissions and group.

Changing the permissions worked right away (using fmask and dmask).

Changing the group via option "gid" however always made the mount options invalid, preventing a successful mount of the USB device.

Filesystem is vfat.

Here are the working mount options:
```
shortname=mixed,uid=,utf8,fmask=117,dmask=007,exec,flush
```

And here, after adding "gid", mount options are invalid:
```
shortname=mixed,uid=,gid=users,utf8,fmask=117,dmask=007,exec,flush
```
Using the numeric ID instead of group name had no effect.

Is there anything I have overlooked in the mount manual?
Are there options combinations that are not allowed?

How do I get the mount options set valid, so I can mount USB devices with group permissions for "users"?

ByteDoc

---

