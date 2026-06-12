---
title: "umask not respected in new install of ubuntu 18.04.3"
date: 2019-09-09
forum: Desktop Environments
---

### Post by entropy1 on 2019-09-09
I have the command ```
umask 077
``` in .profile, .bashrc, and .gnomerc in my home folder. By when I save or create files with TeXStudio, the permissions are ```
-rw-r--r--
```. When I save files using leafpad or vi in the terminal, they are saved with permissions ```
-rw-------
``` which is what I want. How can I fix the behavior of TeXStudio?

---

### Post by TheFu on 2019-09-09
Did you logout and login again so the new session will see the new umask?

---

### Post by entropy1 on 2019-09-14
I actually rebooted, and that seems to have solved the problem.

Thank you!

---

