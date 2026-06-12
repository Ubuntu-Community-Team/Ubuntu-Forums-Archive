---
title: "Ubuntu 8.10 automatic upgrades under non admin user ?"
date: 2009-03-31
forum: General Help
---

### Post by raqua1 on 2009-03-31
I recently installed Ubuntu 8.10 for a friend of mine. she is working under non-admin account, but today she wrote to me, that system asked her to restart due to updates. This seems weird to me, because I am sure I set her account so, that she can not trigger any updates? Does Ubuntu patch itself with some security updates even without the computer admin approval ?

---

### Post by James_Lochhead on 2009-03-31
It can.

Look under System > Administration > Software Sources > Updates

---

### Post by 3rdalbum on 2009-03-31
The Update Manager daemon process runs as root, because checking for updates and writing to the package list is something only root can do. So it's not a case of "automatic upgrades under non admin user" :-)

If your settings allow automatic security updates then this will be done by the update manager daemon too. You can turn this off, but I figure it's a good idea as security updates shouldn't break anything.

---

