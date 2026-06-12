---
title: "the appropriate permission level"
date: 2009-05-08
forum: General Help
---

### Post by GreenLeader on 2009-05-08
When I try to open several folders it says that I do not have the appropriate permission level. This includes "Lost and Found" and "root" folders. I am the only user and admin on the machine and the Unbuntu is a fresh load.

---

### Post by CatKiller on 2009-05-08
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by kanikilu on 2009-05-08
That's how it's supposed to be.

In addition to the URL in the preceding post, you might also want to check out this page:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Also, just in case you were thinking of doing something like recursively changing the permissions or ownership of the whole partition, **don't**, it'll basically break your installation...

If you want to browse file's and folders that you don't have access to, you can temporarily access them by either typing ```
gksu nautilus
``` in a terminal.

If you prefer to have a more "integrated" way to do it, install the **nautilus-gksu** package from Synaptic and then you can right click on a file/folder in nautilus, and you'll have an "Open as administrator" option available in the context menu.

---

