---
title: "open directory as root"
date: 2020-08-25
forum: Desktop Environments
---

### Post by jarp53 on 2020-08-25
I follow the instruction  from "  [https://www.explorelinux.com/open-directory-root-privilege-ubuntu-20-04-lts/](https://www.explorelinux.com/open-directory-root-privilege-ubuntu-20-04-lts/) " to be able to open a directory as administrator but so far is not working , what can I do

---

### Post by deadflowr on 2020-08-25
Are you really using Xubuntu?
If so, this doesn't work on that,
as Xubuntu doesn't use nautilus.

---

### Post by jarp53 on 2020-08-25
ok thanks

---

### Post by The Cog on 2020-08-25
If you're using Xubuntu then "sudo thunar" will probably work (I'm not at home to try right now).

---

### Post by cmcanulty on 2020-08-25
sudo will work but the new way is supposed to be```
 pkexec thunar
```

---

### Post by sisco311 on 2020-08-25
In many GUI applications like nautilus, thunar or gedit you can access privileged files and directories through  GVFS by specifying the admin backend. Just prepend the path in the address-bar with **admin://**, e.g. admin:///root

---

