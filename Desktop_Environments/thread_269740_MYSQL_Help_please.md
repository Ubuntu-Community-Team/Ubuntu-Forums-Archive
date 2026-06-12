---
title: "MYSQL Help please"
date: 2006-10-02
forum: Desktop Environments
---

### Post by Digital221 on 2006-10-02
HI, I was wondering if anyone had a guide to setting up MySQL database to allow a remote machine to make changes to the database. Any idea where i should start looking for this guide? Thanks :)

---

### Post by adwait on 2006-10-02
Well once you have installed MySql, you need to grant a user the previleges to login from any ip eg:
```
grant all previleges ont *.* to root@% grant option
```

the % sign stands for all, otherwise you would have to specify a domain. Check[url]
http://dev.mysql.com/doc/refman/5.0/en/grant.html[/url] for more info.

---

### Post by az on 2006-10-02
I don't think you want to allow remote root access for everybody, eh?

See here to get mysql to listen for connections from the network:

[https://help.ubuntu.com/community/ApacheMySQLPHP#head-2b91cc1ce37842102d20e88e029477b035bee150](https://help.ubuntu.com/community/ApacheMySQLPHP#head-2b91cc1ce37842102d20e88e029477b035bee150)

---

### Post by Digital221 on 2006-10-02
thankyou. but where do i put that code?

---

### Post by adwait on 2006-10-02
Start up mysql with
```
mysql -u root <password i any>
```
Now type that code over there....

---

