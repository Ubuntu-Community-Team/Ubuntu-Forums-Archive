---
title: "php,mysql and http"
date: 2006-01-04
forum: General Help
---

### Post by bigguy on 2006-01-04
How would I or is there away to set up a server on ubuntu 5.10 so I can run a smf 1.1rc2 forum off my computer ???

I`m a noob with linux so be gentle. :D

---

### Post by bigguy on 2006-01-04
Does anyone know ???

---

### Post by melfyk on 2006-01-04
I recommend checking out [http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-database-server]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-database-server")

This guide will show you how to set up mysql, php, and apache from start to finish, better than I can. ;)

---

### Post by bigguy on 2006-01-05
Ok I`ll check that out, thanks.

---

### Post by bigguy on 2006-01-30
When I try to add a file to the "www" folder in apache2 it says I dont have permission to write to that folder. What can I do. Is there a gui for apache, I`m lost here :-k

---

### Post by zkissane on 2006-01-30
There are a couple of solutions here.

For a one time operation you can just use sudo to put the file there.

A more permanent solution would be to add your normal userid to the www-data group (or maybe it's www; I don't know).  Issue ```
ls -la /var
```

Find the "www" entry.  You'll see something like: ```
drwxrwxr-x   4 www-data www   4096 2006-01-29 22:24 www
```

The "www-data" is the owner of that directory, the first "www" is the group that is associated with it, and the drwxrwxr-x are the permissions.  In the permissions, "d" means it's a directory, the first "rwx" means that the owner (www-data) has read, write and execute permissions, the second "rwx" means that the group (www) has read, write and execute permissions, and the "r-x" means that everybody else just has read and execute permissions.  If the group has write permissions to that directory, you can add your normal userid to that group and be able to write to it.  Look up the man page for usermod for help.

---

