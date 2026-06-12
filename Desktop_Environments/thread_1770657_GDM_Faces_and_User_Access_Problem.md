---
title: "GDM Faces and User Access Problem"
date: 2011-05-29
forum: Desktop Environments
---

### Post by rich-brun on 2011-05-29
I've got Ubuntu 11.04 installed. My users' home folders are only  accessible to the users (e.g. chmod 770 /home/*), which means that GDM cannot  access the /home/*/.face file. The permissions are configured (by default)  to allow everyone access to the /var/cache/gdm/*/face files. However,  the login screen will only ever show the user faces when I lower the  permissions on their home folders to allow everyone, including GDM, access to the  /home/*/.face files.

Any thoughts how I can force the login screen to use the /var/cache/gdm/*/face files?

Many thanks,

Rich.

---

### Post by Milan Knizek on 2011-08-11
By any chance, have you found a solution?

---

