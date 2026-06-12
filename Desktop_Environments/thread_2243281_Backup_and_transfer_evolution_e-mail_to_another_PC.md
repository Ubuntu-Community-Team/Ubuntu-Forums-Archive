---
title: "Backup and transfer evolution e-mail to another PC"
date: 2014-09-07
forum: Desktop Environments
---

### Post by cigtoxdoc on 2014-09-07
How does one transfer Evolution e-mail 3.10.4 to anolther PC when each time I use the Evolution back-up function it either terminates without making the correctly-sized backup file or it creates a backup file which Evolution says is invalid?

Thank you,

John

---

### Post by cigtoxdoc on 2014-09-08
I took some time to figure out what was going on:  Following the backup and restore instructions exactly as written always resulted in an "invalid backup file."  Why was the backup file invalid?  There was an error in the folders.db database file.

Once I did the follwing, I was able to create a vaid backup file and successfully restore it on another PC.

Here are the steps:

1. Open a terminal and type sudo su
2. Enter sudo password and change directories until you get to /home/username/.local/share/evolution/mail/local.
3. When you are at  /home/username/.local/share/evolution/mail/local$, enter sqlite3 folders.db "pragma integrity_check;"
4. Terminal should return "ok"
5. Kill all evolution-related processes.
6. Delete folders.db or rename it to folders.dbb
7. Restart evolution

Please note that it will take time (better part of 20 minutes) for evolution to repopulate all the folders.

Now you are ready to Backup evolution data.

I would appreciate feedback from other users with same problem.

John

---

