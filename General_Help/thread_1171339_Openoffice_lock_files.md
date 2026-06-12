---
title: "Openoffice lock files"
date: 2009-05-27
forum: General Help
---

### Post by lgiordani on 2009-05-27
Hi all,

I'm using Openoffice 3.0.1 on Kubuntu Jaunty to edit files stored on an sshfs disc and run into the well known problem of OO lock files over NFS (this is sshfs, but the problems are the same).

I tried to disable lock files creation through editing /etc/openoffice/soffice.sh and setting

```

FILE_LOCKING=no

```

which is read by the file /usr/bin/soffice (link to /usr/lib/openoffice/program/soffice) which sets the environment variable SAL_ENABLE_FILE_LOCKING to 0 (I checked it).

But OO seems to ignore it: if I open a file OO creates the lock file.

Someone already noticed this behaviour? Someone solved it?
Thank you in advance

Leonardo Giordani

PS: sorry if the forum section is wrong.

---

### Post by Michael REMY on 2009-06-23
hi !

+1

i have the same problem !

any idea to solve it ?

---

