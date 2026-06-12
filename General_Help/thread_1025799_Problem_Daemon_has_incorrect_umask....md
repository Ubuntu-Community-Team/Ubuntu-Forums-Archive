---
title: "Problem: Daemon has incorrect umask...?"
date: 2008-12-30
forum: General Help
---

### Post by Elchbulle on 2008-12-30
I may be completely wrong here, but for some reason one of my daemons appears to have the incorrect umask set.  The daemon is hellanzb, a binary usenet fetcher.

Whenever it downloads something it unrar's it and places it in /storage

No matter what the umask is for /storage the folders and files are created with 700 rwx------ permissions.  This makes is extremely annoying when I try to get some of the files across a network.  I have to manually change the permissions every time something new is created.  However, when I manually create a folder or file it has the correct permissions.

How can I check to see why hellanzb / unrar is creating files with the 700 permissions?!

Thanks for any and all help!   :confused:

---

