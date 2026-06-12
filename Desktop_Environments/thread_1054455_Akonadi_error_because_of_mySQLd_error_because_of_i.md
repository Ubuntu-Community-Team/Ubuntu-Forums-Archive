---
title: "Akonadi error because of mySQLd error because of innoDB error."
date: 2009-01-29
forum: Desktop Environments
---

### Post by Harikawashi on 2009-01-29
Just upgraded to KDE4.2
It seems now KMail wants to use Akonadi, but Akonadi cannot start. It directs me to the MySQL server log, which contains:

090129 15:33:01 InnoDB: Operating system error number 2 in a file operation.
InnoDB: The error means the system cannot find the path specified.
InnoDB: If you are installing InnoDB, remember that you must create
InnoDB: directories yourself, InnoDB does not create them.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.

I'm totally stuck, can't find anything on google. Does anybody have ANY suggestions?

---

### Post by gogh on 2009-02-22
> **Harikawashi said:**
> Just upgraded to KDE4.2
It seems now KMail wants to use Akonadi, but Akonadi cannot start. It directs me to the MySQL server log, which contains:

090129 15:33:01 InnoDB: Operating system error number 2 in a file operation.
InnoDB: The error means the system cannot find the path specified.
InnoDB: If you are installing InnoDB, remember that you must create
InnoDB: directories yourself, InnoDB does not create them.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.

I'm totally stuck, can't find anything on google. Does anybody have ANY suggestions?

I have exactly the same problem. Did you find a workaround?

---

### Post by Harikawashi on 2009-02-24
Not yet

---

### Post by Harikawashi on 2009-02-24
This thread describes the problem in more detail:
[http://www.kde-forum.org/post/74497/please-help-no-kmail-because-of-akonadi-error-because-of-innodb-error.html#post74497](http://www.kde-forum.org/post/74497/please-help-no-kmail-because-of-akonadi-error-because-of-innodb-error.html#post74497)

---

### Post by sonicb00m on 2009-02-28
I've done a fresh install and it is still broken.

---

### Post by sonicb00m on 2009-03-01
Problem seems to be because of an encrypted home folder.

I reinstalled it and it's working fine now.

---

