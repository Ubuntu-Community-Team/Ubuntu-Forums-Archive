---
title: "MySQL problems"
date: 2006-01-05
forum: General Help
---

### Post by Newbify2 on 2006-01-05
I've searched through this forum and tried everything, nothing seems to work, any help would be greatly appreciated.

I've done:

sudo apt-get install mysql-server

when I try:
```
mysqladmin -u root password 'password'
```
or
```
mysqladmin -u root password -p
```

I get:

```
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: YES)'

```

My /etc/hosts file looks like this
```
127.0.0.1       localhost       localhost.localdomain   winston
```

And of course:
```
mysql -u root -p
```
only returns:
```
ERROR 1045: Access denied for user: 'root@localhost' (Using password: YES)
```

Any ideas? [edit] btw I'm using Breezy... [/edit]

---

### Post by faulkner132 on 2006-01-05
When I set mine up, I used the mysql-server-4.1 and mysql-administrator (<- can't remember if that is the exact name).
Maybe try that instead?

---

### Post by Newbify2 on 2006-01-05
Worked perfectly, thanks for your help.

I removed mysql-server and installed the new one and mysqladmin -u root password 'asdfasdf' worked just fine.

---

