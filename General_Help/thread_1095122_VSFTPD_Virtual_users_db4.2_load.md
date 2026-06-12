---
title: "VSFTPD Virtual users db4.2_load"
date: 2009-03-13
forum: General Help
---

### Post by artheus on 2009-03-13
Hello!
I am trying to create virtual users for my vsftpd.

I am currently following this:
[ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.3/EXAMPLE/VIRTUAL_USERS/README]("ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.3/EXAMPLE/VIRTUAL_USERS/README")

and this thread in this forum :
[http://ubuntuforums.org/showthread.php?t=34292]("http://ubuntuforums.org/showthread.php?t=34292")

I saw the last post in that thread, which tells me I should use

sudo db4.2_load -T -t hash -f logins.txt /etc/vsftpd_login.db

instead of any of the earlier versions.
But it won't work with the "-T", and without the "-T" it does not recognize the filetype of my logins.txt. I created logins.txt using pico, and writing :

"
test1
1234
test2
1234
"

But I get the answer "db_load: line 1: unexpected format".

What can I do to make that work?


Cheers,
Artheus

---

### Post by artheus on 2009-03-14
Well.. after a reboot.. it worked..

---

