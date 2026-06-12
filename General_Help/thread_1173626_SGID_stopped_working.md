---
title: "SGID stopped working"
date: 2009-05-29
forum: General Help
---

### Post by diogobaeder on 2009-05-29
Guys,

SGID stopped working for me. I want to share a directory with everyone at my local network, with no restrictions (full read/write access), but SGID is not setting the default directory mode as it should. Here's an example of the commands showing the problem I've run into:

```

diogo@diogo-desktop:/share$ ls -lha
total 32K
drwxrwsrwx  5 root  sambashare 4,0K 2009-05-30 00:26 .
drwxr-xr-x 22 root  root       4,0K 2009-05-29 14:02 ..
drwxrwsrwx  4 clara sambashare 4,0K 2009-05-26 22:48 fotos_clara
drwxrwsrwx  2 root  sambashare  16K 2009-05-12 04:00 lost+found
drwxrwsrwx  4 clara sambashare 4,0K 2009-05-28 13:36 .Trash-1001
diogo@diogo-desktop:/share$ sudo chmod g+rwxs .
diogo@diogo-desktop:/share$ touch why_not_others
diogo@diogo-desktop:/share$ ls -lha
total 32K
drwxrwsrwx  5 root  sambashare 4,0K 2009-05-30 00:30 .
drwxr-xr-x 22 root  root       4,0K 2009-05-29 14:02 ..
drwxrwsrwx  4 clara sambashare 4,0K 2009-05-26 22:48 fotos_clara
drwxrwsrwx  2 root  sambashare  16K 2009-05-12 04:00 lost+found
drwxrwsrwx  4 clara sambashare 4,0K 2009-05-28 13:36 .Trash-1001
-rw-r--r--  1 diogo sambashare    0 2009-05-30 00:30 why_not_others
diogo@diogo-desktop:/share$ 

```

Note that the "why_not_others" file should have a rws group permission, but it doesn't. Am I doing something wrong here?

Thanks!

Diogo

---

### Post by kidders on 2009-05-31
Hi there,

> **diogobaeder said:**
> Note that the "why_not_others" file should have a rws group permissionNot necessarily. Setting the SGID bit on your /share directory sets the default group *ownership* of new files. What permissions those files have is a completely separate issue, determined by the environment's umask.

Generally, you can't force users to allow/deny access to files they create.

---

### Post by diogobaeder on 2009-05-31
Kidders,

I noticed that I indeed confused file ownership with file permissions...

Well, let me explain my problem: I've got an entire partition, mounted as "/share", that I wish to share simultaneously with the Linux users at my machine and the local network users, at home, with all permissions for everybody there. The thing is: as a Linux user creates a file there, the applied write permission is only for the user, and, while the group is set to the one I want ("sambashare"), its permission is read-only.

So, how can I prepare the mount to apply, by default, read-write-execution permissions for all files put in there? Is mounting as a smbfs for the local users the only way to accomplish that? Because it seems a little dumb, to me, to mount a Samba partition if it is in the same machine that the Linux users, despite the fact that it would indeed work for all...

Thanks!

Diogo

---

### Post by kidders on 2009-05-31
> **diogobaeder said:**
> So, how can I prepare the mount to apply, by default, read-write-execution permissions for all files put in there?In general, you can't ... at least not on a per-directory basis. The only thing that normally influences the default permissions applied to a new file is the umask set in the environment that created it. Users are free to set their umask to whatever they want. Far from being dumb, Linux works this way for very good reasons. For example, what you want to set up would make it possible to acquire access to a file simply by moving it into a different directory. Naturally, no good filesystem security model would allow that sort of thing.

As you pointed out, Samba can be configured to chmod new files as it creates them, in an effort to get Linux's filesystem permissions to roughly match the Windows ones on the other end of the share. That facility is necessary because Linux & Windows permissions aren't equivalent, so it's quite easy to get tangled up in knots.

It sounds to me like you may not care about permissions at all. If you want everyone to be able to read/write/execute everything, then you might as well choose a filesystem with no permissions support (or one that can at least let you turn it off, eg HFS).

---

