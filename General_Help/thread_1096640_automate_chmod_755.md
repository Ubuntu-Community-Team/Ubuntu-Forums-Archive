---
title: "automate chmod 755"
date: 2009-03-15
forum: General Help
---

### Post by artheus on 2009-03-15
Hey!

I have the problem that I want to use my Apache2 and VSFTPD to use the same folder. So that I can use my server as an easy testserver.
But when I upload my eg. *.htm files to the server the previleges ar totally wrong. So I can't see the files in the browser. The browser just says something like "404 Forbidden" (or 402 or whatever it is).
But when I change the previleges/permissions to 755 it works fine. But I now have many files I want to change the permissions on at the same time. About 20 files or so.

So is there any way to make the vsftpd change the permissions of the files uploaded to 755 automatically (when uploaded)?

Cheers

---

### Post by namaku0 on 2009-03-15
Maybe you want to read this first: [http://en.wikipedia.org/wiki/Umask](http://en.wikipedia.org/wiki/Umask)

Please note that some FTP server/client let you set
the default permission. So you may want to check your
FTP server/client configuration too.

---

### Post by artheus on 2009-03-15
Thanks alot namaku0!
I found a default umask setting (local_umask) in the vsftpd config file (/etc/vsftpd.conf) and changed it to 022. And now it works perfectly!

Thanks again!

---

