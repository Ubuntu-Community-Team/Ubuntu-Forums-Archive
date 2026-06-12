---
title: "Emacs file permission"
date: 2010-09-26
forum: Desktop Environments
---

### Post by mcfanda on 2010-09-26
Hi
I noticed my emacs on ubuntu 10.04 (it never did it before 10.04) changes the permissions of remote files that I edit. I usually edit files on a remote server after mounting a remote dir via sftp. The files on the remote system are owner by root and 0775. I'm member of the file group. When I save them from my emacs, the owner become my user, and 0770. Any help?
mc

---

### Post by Chesamo on 2010-09-27
emacs saves files by moving the old one to filename~ and creating a new file. I *thought* that emacs retained the same owner/permissions in the new file as on the old file, but I guess smomething changed recently. Might want to file a bug report with the emacs team, since I can reproduce this problem.

---

### Post by worseisworser on 2011-06-11
I'm having the same issue over here on version 24.0.50.1. Did you guys report a bug?

Emacs is the only editor with this behavior; it's quite a problem when working on a shared directory.

---

