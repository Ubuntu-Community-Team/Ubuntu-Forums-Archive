---
title: "folder permissions"
date: 2006-06-22
forum: Desktop Environments
---

### Post by drs101 on 2006-06-22
I have just installed Ubuntu 6.06 desktop, with apache, mysql, php and proftpd.
Now all seems to be working fine but when I connect by ftp using my ubuntu login and password and navigate to /var/www/ I cannot change or upload any files.

I assume this is to do with permissions, but I have no idea where to start, 
any help would be great.

Danny

---

### Post by thasheep on 2006-06-22
If you're the only one who needs write access, then you could change the ownership of /var/www
```
sudo chown -R $USER:$USER /var/www
```

---

### Post by drs101 on 2006-06-22
thanks

Danny

---

### Post by drs101 on 2006-06-22
thanks

Danny

---

