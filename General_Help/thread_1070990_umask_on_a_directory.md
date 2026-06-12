---
title: "umask on a directory"
date: 2009-02-15
forum: General Help
---

### Post by dread22 on 2009-02-15
I need to have one folder which must have all that are created able to be written to by anyone in the group. So I'll need file permissions like
rwxrwxr-x   2 root mygrp  4096 2009-02-16 09:59 /home/mygrp/file
now I know you can set the umask flag to 002 to do this but I need this umask to be set automatically for any new users to the group. I don't really want the new user to go into their bashrc file.

---

