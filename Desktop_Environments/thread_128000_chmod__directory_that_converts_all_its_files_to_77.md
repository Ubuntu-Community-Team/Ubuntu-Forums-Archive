---
title: "chmod / directory that converts all its files to 777 permissions!! Help me, please!"
date: 2006-02-10
forum: Desktop Environments
---

### Post by jpincheira on 2006-02-10
hi guys, I need to set up permissions to a directory, so I need that other users can delete o create files on /var/files. But I cannot get it running, which command have I to do to get that directory readeable and writable, and when a user creates a file on that directory, other user can delete it, so the files that those users created acquire all the permissions (777) like a mask on that directory...

an example:

I have a ltsp server, so I have a directory for shared files /var/compartidos and I want every file that's created there by system users converts to 777 permissions.

help me guys! Thanks!

---

### Post by alfonz on 2006-02-10
not sure if this works for directories but for a file command is

```
sudo chmod 777 <name>
```

---

### Post by jpincheira on 2006-02-10
I have a directory for shared files /var/compartidos and I want every file that's created there by system users converts to 777 permissions.

That's something like a mask. Not just an ordinary chmod, dude.

Please help me!

---

### Post by nihilocrat on 2006-02-10
umask 777, right?
I'm not exactly sure how ltsp works, but wherever there is something similar to a .bashrc or .bash_profile file, add 'umask 777' to it.

To get ALL the existing files and subdirectories to 777, make sure to do "chmod -R 777"

---

