---
title: "Apache help with symlinks"
date: 2006-01-16
forum: General Help
---

### Post by _jane_ on 2006-01-16
I installed the Apache server and it works just fine. A Problem recently occurred as  I tried linking some of the files I have on my old ntsf windows-partition. The symlinks are owned by root but they do not seem to appear in my web-page. Can anyone help me with this one?
The web page works just fine when I create a text-file in the /var/www-folder or if I copy something from the windows-partition to the /var/www-folder but I would like to only link them so that I wouldn´t be having to have the same files in multiple places.

---

### Post by lcg on 2006-01-16
> **_jane_]I installed the Apache server and it works just fine. A Problem recently occurred as  I tried linking some of the files I have on my old ntsf windows-partition. The symlinks are owned by root but they do not seem to appear in my web-page. Can anyone help me with this one?[/QUOTE]
Google could have helped you ... It often can. You should give it a try.  said:**
> The web page works just fine when I create a text-file in the /var/www-folder or if I copy something from the windows-partition to the /var/www-folder but I would like to only link them so that I wouldn&#180;t be having to have the same files in multiple places.
Have a look at the Options directive in the [Apache documentation]("http://httpd.apache.org/docs/2.0/de/mod/core.html#options"), especially the FollowSymLinks part.

HTH,
Lars

---

### Post by _jane_ on 2006-01-16
Ok. Now I know what to do. How do I get there? How do I set/change a variable in apache. I´m an absolute beginner. Please help.

---

