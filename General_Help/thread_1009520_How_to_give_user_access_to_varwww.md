---
title: "How to give user access to var/www?"
date: 2008-12-12
forum: General Help
---

### Post by NeoID on 2008-12-12
I've just installed Ubuntu server with Apache and everything works quite well. However, just a question.. how may I give the user created on the Ubuntu install read and write permission to the www-folder (and everything within)?

The www-folder is owned by www-data...
```
chown -R www-data:www-data /var/www
```

Should I add the user to the www-data group or what should I do?

---

### Post by marshall.robert on 2008-12-12
just go 

```

sudo chown -R User /var/www

```

thats all i did...

just remeber its case sensitive, like almost all linux things.

---

### Post by NeoID on 2008-12-12
> **marshall.robert said:**
> just go 

```

sudo chown -R User /var/www

```

thats all i did...

just remeber its case sensitive, like almost all linux things.

...but will apache (www-data) still have access to the folder if I change the owner?

---

### Post by Iowan on 2008-12-12
I've been wrong before, but it should still work even if ownership changes.
OR... you could add the user to the www-data group.
OR... you could build another website with document root somewhere else.

---

### Post by spiderbatdad on 2008-12-12
why change ownership? why not make the directory and whatever files writable? ```
sudo chmod go=rw /var/www
```
I prefer not to recommend -R option. Instead treat files individually.

---

### Post by NeoID on 2008-12-13
> **spiderbatdad said:**
> why change ownership? why not make the directory and whatever files writable? ```
sudo chmod go=rw /var/www
```
I prefer not to recommend -R option. Instead treat files individually.

I've tried that... now I can't even list the dir -_-
> Command 'cd "/var/www/"'
failed with return code 1 and error message
-bash: line 34: cd: /var/www/: Permission denied.

How can I revert the change? ._.

---

### Post by spiderbatdad on 2008-12-13
Please make note of existing permissions before changing them. To see the permissions of a directory: ```
ls -l /var
```The orignial permissions were likely: 755. This is read,write,execute for owner; read,execute for group; read,execute for others....shown at the left as, d(directory)rwxr-xr-x. You now have drwxrw-rw-. To make the directory globally writable/executable: ```
sudo chmod 777 /var/www
```Sorry you had the problem. Check here for much more about permissions. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I should have told you: ```
 sudo chmod a+w /var/www 
``` this would have simply added write permission to all 3 groups rather than defining group/other as rw, and removing x. Again sorry, now the truth comes out...I am not perfect.

---

### Post by fguilhon on 2008-12-13
The chmod go+rw (with the plus sign not equal sign) is a good solution for a test environment.
If it were a production env. it would be safer to give permissions on a subdir basis..

---

