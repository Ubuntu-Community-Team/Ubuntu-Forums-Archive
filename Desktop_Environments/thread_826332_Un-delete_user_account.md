---
title: "Un-delete user account?"
date: 2008-06-11
forum: Desktop Environments
---

### Post by jbrunton on 2008-06-11
I deleted a user account but not the home directory.

Is it possible to create the same account, again, and re-attach the home directory?

---

### Post by tamoneya on 2008-06-11
yes:```
sudo useradd -d /home/oldusername/ newusername
``` newusername and oldsudername can be the same if you like.

---

### Post by jbrunton on 2008-06-11
I must have more problems than I thought. I got these two errors when I tried logging in using the restored account:

1. User's $HOME/.dmre file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

(I did a search on the file system and couldn't find a file like .dmre)

2. The GNOME session manager was unable to lock the file '/home/username//.ICEauthority'. Please report this as a GNOME bug. Sometimes this error may occurs if the file's directory is unwritable, you could try logging in via failsafe session and ensuring that it is.

(also did a search for .ICEauthority on the file system and couldn't find it)

---

### Post by tamoneya on 2008-06-11
change the permissions/ownership of the folder:```
sudo chown -R newuser /home/olduser
```

---

### Post by molotov00 on 2008-06-11
Alternatively, create the user with empty home dir, copy files over, then chown.

---

### Post by jbrunton on 2008-06-12
Thanks tamoneya!

This has put my life back in order. All my settings are exactly as they were and all my preferences are as they were.


This has been most helpful.

Thank you so much!

---

