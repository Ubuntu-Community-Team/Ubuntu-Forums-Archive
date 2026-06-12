---
title: "Unable to copy to external hard disk, please help"
date: 2009-05-24
forum: General Help
---

### Post by yizsa on 2009-05-24
Hi,
I wanted to copy some files to an external hard disk, but was not allowed.
Under Properties>Permissions>Owner: root
and it says 'not the owner, can't change these permissions.'
I tried the chmod command, but it gave another message: read-only file system.
I'm not sure if I'm doing anything wrong?

Please help.

---

### Post by Minsky on 2009-05-24
Try **sudo chown -R _username_:_username_ /path/to/external/drive**   and see if that works

---

