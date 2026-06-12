---
title: "gedit changes owner and group of file"
date: 2008-09-01
forum: Desktop Environments
---

### Post by chenel on 2008-09-01
Does anybody know how to force gedit to retain the original owner and group of a file when saving it?  

I have several files on my web server that need to be readable by the apache user (www-data) but also editable by web author users.  I don't want them world-readable, however, as it's a security risk for the contents of those particular files, so they are owned by www-data, and are assigned to the 'admin' group (of which I'm a member), with -rw-rw---- permissions.  

However: every time I use gedit to modify them, they wind up back with me as the owner and the group assigned to my user group!  (Fortunately the permissions stay the same.)  It's very irritating to have to go in and manually change the permissions back every single time I make a modification.  I wasn't able to find any help on Google.

Any thoughts?

---

### Post by vanadium on 2008-09-01
This was an issue with gedit in early Gutsy that was solved. See our discussion of almost a year ago, [http://ubuntuforums.org/showthread.php?t=572535&highlight=gedit+permissions](http://ubuntuforums.org/showthread.php?t=572535&highlight=gedit+permissions)

For me, it currently works correctly.

---

### Post by chenel on 2008-09-01
Strange.  I am running Hardy (and have been since its release).

Do you know what version of gedit fixed it?

---

### Post by chenel on 2008-09-01
Addendum:

Perhaps this is the difference.  I usually use gedit to edit files over ssh (that is, I edit files like sftp://user@host/var/www/....).  I did your little test, and it seems to maintain users and permissions fine locally on my machine, but on the remote host it messes things up.

Is this a new version of that bug, then?

---

### Post by vanadium on 2008-09-02
I have notified the gnome developpers: [http://bugzilla.gnome.org/process_bug.cgi](http://bugzilla.gnome.org/process_bug.cgi)
This is a similar ill behaviour that persists for remote files. nano does not have this issue.

---

### Post by leifharmsen on 2011-03-19
bump

It's 2011 and gedit is changing the group from www-data to my userid group every time I save a file, and I have to ssh in with a terminal and change it back - very annoying and time consuming!  I've googled my face off and can find no solution.  Anyone know what is causing this or better still, know some way of fixing it?

---

### Post by mxsteini on 2011-07-31
have the same problem.
Really anoying.
:(

---

### Post by leifharmsen on 2012-01-04
Bump again for 2012!  

I'll be bumping this every year- it's a high priority bug if you maintain code on a server and do it all the way that's prescribed to "just work" in Ubuntu 10.04 LTS... with ssh via Nautilus' GUI file browser and gedit. The LTS isn't meant to be bleeding edge.   The editor has no business changing the group owner of a file, it's potentially a security issue, so why does it do it and how can I stop it?  Anyone?  Is there a similar editor to gedit that doesn't mess with the group of the file?   How could I notify the gedit developers about this?  This isn't my area of expertise.

---

### Post by wildmanne39 on 2012-01-04
Hi, how are you running gedit with sudo? if so you need to run all graphical applications with gksu or gksudo to make sure root does not take ownership and if this is the case it is not a bug, here is a link.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Thanks

---

### Post by chenel on 2012-01-05
Hi,

The problem this thread is discussing actually has nothing to do with sudo (or the root user at all for that matter).  The canonical situation is one like the following:

 File 'FILE' exists on machine MACHINE1 with owner USER1, group GROUP, and permissions rw-rw-r--:

```
 $ ls -l FILE

 -rw-rw-r-- 1 USER1 GROUP 12345 2012-01-01 00:00 FILE

```
 User USER2, who is a member of GROUP, edits FILE over SFTP using gedit (since the file is group-writable).

 After editing, the file owner changes!:

 ```
$ ls -l FILE

 -rw-rw-r-- 1 USER2 GROUP 12345 2012-01-01 01:23 FILE

```

The use case in which I encounter it is when I am editing code for a web server, which is owned by user "www-data" and group-writable by "web-admin".  It should remain owned by www-data after editing, but it changes to my personal user (who is a member of www-data).  This shouldn't happen!

Hope this clarifies the issue.

---

### Post by tyzoid on 2012-07-13
Same problem here, in July of 2012

-rwxrwxr-- 1 user www-data 337 2012-07-13 13:11 code.php
     - gets changed to -
-rwxrwxr-- 1 user user 337 2012-07-13 13:11 code.php

upon editing

---

### Post by wildmanne39 on 2012-07-13
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

