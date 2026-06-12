---
title: "Troubles with symbolic link file permissions"
date: 2006-08-12
forum: Desktop Environments
---

### Post by Gotou on 2006-08-12
Hi! I'm learning how to make symbolic links but I've run into a snag.  I'm trying to create a one-word link (to use in the terminal) to a program file buried in the .wine directory.  After the symbolic link is created the file permissions for it are wide open.  Owner,group and other have full rwx.  When I try to change the file permissions by right clicking on the link > properties > permissions I get a "Sorry, unable to change permissions" error message.  I then tried to  sudo chmod 775, but that had no affect either.

Any ideas?

Thanks in advance.

---

### Post by llamakc on 2006-08-12
Don't sweat it. If the file linked to has the permissions you want, you'll be A-okay.

---

### Post by Gotou on 2006-08-12
Hmm, the original file's permissions.  That hadn't occured to me.  Thanks!

---

