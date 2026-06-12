---
title: "how to change folder permissions for folders under lib/mysql"
date: 2009-03-06
forum: Desktop Environments
---

### Post by raunhar on 2009-03-06
how to change folder permissions for folders under lib/mysql

I need to view the contents of the mysql folders created under var/lib/mysql

Please suggest.

---

### Post by Lord Landis on 2009-03-08
Changing the folder permissions would be bad - you should probably not do that.

A quick 'ls' from the command line will generally show you what you're looking for.  Just execute the following:

```
ls /var/lib/mysql
```

If that command gives you a permission denied error, then run it again, but use sudo.

---

### Post by warp99 on 2009-03-08
> **raunhar said:**
> how to change folder permissions for folders under lib/mysql

I need to view the contents of the mysql folders created under var/lib/mysql

Please suggest.

Changing the permissions is not needed but you most likely need to add the mysql group to your user name.

Edit:

Use the following to add the group:
```
 sudo adduser <user_name> mysql
```
Logout and back in again. The mysql group will be added to you user name. You can then view the contents of the mysql directory.

---

### Post by raunhar on 2009-03-09
Will check it and reply back.

---

### Post by raunhar on 2009-03-09
sorry did not work out. If I go to var/lib/mysql/abc and then check the permissions for abc, it shows, you are not the owner, so cannot access.

I had did this 
sudo adduser name mysql


Pl. confirm.

---

### Post by warp99 on 2009-03-09
Did you replace "name" with your user name? You should have access to the folder since the files are owned by mysql:mysql. If the permissions were changed issue the following to restore:

```
sudo chmod 755 /var/lib/mysql
```

---

