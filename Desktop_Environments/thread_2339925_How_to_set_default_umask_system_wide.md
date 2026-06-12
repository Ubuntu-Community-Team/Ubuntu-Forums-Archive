---
title: "How to set default umask system wide"
date: 2016-10-14
forum: Desktop Environments
---

### Post by ronaldw2 on 2016-10-14
How do I set the default umask in order to give the group the same permissions as the owner (002)?

If I change the value "UMASK 022" in /etc/login.defs to "UMASK 002" it does not change anything. (I rebooted after changing the value for the case that a re-login is not sufficient)

When I open a gnome-terminal and type "umask" I get 0022. (why 4 digits here and only 3 in login.defs) When I set the umask by issuing "umask 0002" the creation of files and folders behaves like desired. But - of course - this setting is not permanent and has no influence on how Nautilus sets permissions.

So - how can I set the default umask system wide (for shell, nautilus, applications, nfs, ...)?

---

### Post by &amp;KyT$0P# on 2016-10-14
Does [this]("https://forums.informaction.com/viewtopic.php?f=24&t=22082") help?

---

