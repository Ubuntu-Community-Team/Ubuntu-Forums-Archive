---
title: "Few MySql problems"
date: 2006-02-23
forum: Desktop Environments
---

### Post by imiksu on 2006-02-23
Hi, i'm wondering to know why i can't connect MySql from another computer... I can only connect from localhost...

And second guestion.. I did a big update, don't know what happened :p but after that i notices phpmyadmin didn't worked... Any username and password (witch is right) i try to login, it wont... It says nothing...:confused:

---

### Post by joselin on 2006-02-23
You have to uncoment skip-external-locking on /etc/mysql/my.cnf to allow external conections.

Regards.

---

### Post by imiksu on 2006-02-23
It's allready uncommented :-k

---

### Post by lamego on 2006-02-23
The mysql user access control also works based on the connecting host.
Are you able to connect and getting an user access denied  or you are getting an "unable to connect" ?

---

### Post by imiksu on 2006-02-24
Cannot connect...

---

### Post by Treebeard on 2006-02-24
Uncomment
```

# skip-networking
``` 
Make sure to restart MySQL..

```

$ sudo /etc/init.d/mysqld stop
$ sudo /etc/init.d/mysqld start

```

---

### Post by imiksu on 2006-02-25
Can't find any "# skip-networking" text... In witch file?

---

### Post by tharsan on 2006-04-02
In order to connect from outside the localhost, I needed to edit /etc/mysql/my.conf to comment out the 'skip-networking' line.

---

