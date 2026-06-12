---
title: "User cannot write to htdocs folder, only root can write"
date: 2005-03-06
forum: Desktop Environments
---

### Post by bstil on 2005-03-06
Hello.  I cannot write to my apache htdocs with my desktop user account.  Only root can write from the shell.  Note: I setup apache 1.3 from make install not apt-get.

Text editor on desktop:
Could not save the file "/www/htdocs/test.htm".

Then I added a group "htdocs" and added myself to the group.  I then changed all the files to the group and added group write priv.  But it doesn't work... ?!  What is wrong?  Either I am missing something really obvious or it is an Ubuntu thing?

root@mycomputer:/www/htdocs # ls -al
total 152
drwxrwxr-x    3 root     htdocs      4096 2005-03-06 02:45 .
drwxr-xr-x   12 root     root         4096 2005-03-06 01:36 ..
-rw-rw-r--    1 me    htdocs      2326 1996-07-03 02:18 apache_pb.gif
(a bunch more)
root@mycomputer:/www/htdocs # groups me
me : me adm dialout cdrom floppy audio video plugdev lpadmin scanner htdocs
root@mycomputer:/www/htdocs #

---

### Post by alastair on 2005-03-06
You might need to log out and log back in (at least get a new login shell). Unless I'm mising something obvious!

---

