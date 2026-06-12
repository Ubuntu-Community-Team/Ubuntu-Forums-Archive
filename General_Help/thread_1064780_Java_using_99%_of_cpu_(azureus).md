---
title: "Java using 99% of cpu (azureus)"
date: 2009-02-09
forum: General Help
---

### Post by spinanicky on 2009-02-09
Hi all,

Running Vuze on a headless server installation and periodically (as far as I can tell its daily) java starts using 70-90% of the CPU power. The only way to stop it is by re-starting vuze. 

Does anyone know why this is or why it could be.. its really starting to annoy me.

Also a quick question just incase you know... what should the rwx (chmod) of the www directory be!?

Thanks a lot.

---

### Post by SeanTater on 2009-02-09
I don't use Java or Azureus, so I don't know the answer to question 1, but /var/www should be chmod 0755 which is drwxr-xr-x. The owner and group should both be root.

---

### Post by spinanicky on 2009-02-09
Others should be able to execute... isnt that a bit dangerous?!

---

### Post by SeanTater on 2009-02-09
Not for a folder. In the context of a folder, "executable" means "can list contents".
As for web serving, even an executable *file* is meaningless. Apache won't execute it unless it is configured to, in which case, it would be a CGI.

---

### Post by spinanicky on 2009-02-09
ok, one last point then. In order to write files to the server I use samba.. obviously I can sign in as root to write... so what should I do?! When I try to write with user nicky it wont let me...?!

Thanks for your help

---

### Post by SeanTater on 2009-02-10
Remember, the web server is reading this directory from "other", so you can change the user without effecting the web server.

You could do: ```
sudo chown -R nicky.root /var/www
```
or:```
sudo chown -R nicky.users /var/www
```

They both have approximately the same meaning since group and other have the same permissions.

---

