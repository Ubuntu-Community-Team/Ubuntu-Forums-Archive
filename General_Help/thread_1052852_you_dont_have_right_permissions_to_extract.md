---
title: "you dont have right permissions to extract"
date: 2009-01-28
forum: General Help
---

### Post by Shishant on 2009-01-28
Hello,

I am a windows user and recently trying to shift to ubuntu.

My problem is when i am trying to extract a file in filesystem/var/www, it says i dont have permission, how can i disable this permanently and provide me 100% authorization for everything like in windows xp.

[IMG]http://i39.tinypic.com/28bf8rm.png[/IMG]


Thanks alot...

---

### Post by hyper_ch on 2009-01-28
how is owner of /var/www and what are the permissions set there?

---

### Post by geirha on 2009-01-28
Quickest fix is to make /var/www be owned by you. You can do this either by typing in a terminal:
```
sudo chown $USER /var/www
```

Or by starting nautilus as the root user by hitting alt+f2 to get the run-dialog, run ```
gksu nautilus
```, browse to /var, right-click www and select properties, and set yourself as the owner under the permissions tab.

Having "100% authorization for everything like in windows xp" is highly discouraged. It would make your system very vulnerable.

---

### Post by jespdj on 2009-01-28
> **geirha said:**
> Quickest fix is to make /var/www be owned by you. You can do this either by typing in a terminal:
NO, don't do that! /var/www is not supposed to be owned by you. Don't touch the ownership settings of that directory.

Just use gksu nautilus to unpack the archive using the administrator account.

> **geirha said:**
> Having "100% authorization for everything like in windows xp" is highly discouraged. It would make your system very vulnerable.
I agree, do not try to destroy the security of your system by doing everything with the administrator account or by changing permissions and ownership as you please - this will make your system vulnerable to hackers.

---

### Post by geirha on 2009-01-28
> **jespdj said:**
> NO, don't do that! /var/www is not supposed to be owned by you. Don't touch the ownership settings of that directory.

Just use gksu nautilus to unpack the archive using the administrator account.


No, it's much better and more secure to change the ownership of /var/www, than having to use sudo everytime you want to add or remove files there. One does have to make sure only the users that need write access (web developers) has write access to it though.

---

### Post by hyper_ch on 2009-01-28
> **geirha said:**
> No, it's much better and more secure to change the ownership of /var/www
I disagree. Apache should be owner of that directory.

And you normally don't have that directory on your local machine but normally you use a real server. In that case you will login accordingly on the server to conduct the changes.

---

### Post by Shishant on 2009-01-28
Thanks alot....................

---

