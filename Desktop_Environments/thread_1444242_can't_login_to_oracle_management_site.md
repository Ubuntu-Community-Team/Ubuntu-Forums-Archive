---
title: "can't login to oracle management site"
date: 2010-04-01
forum: Desktop Environments
---

### Post by caymahallesi on 2010-04-01
Hi 
I installed my oraclexe with the instructions shown here;
[http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html](http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html)

after the installation and configuration is finished
I used this url to login to management site.
[http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex)

however every time I tried to login with "system" user name and my password which I created during installation of oracleXe. Doesn't work. It says "Invalid login credentials."

Now. I am new to Ubuntu and Oracle. So, can anybody tell me if I am doing wrong?

or is there something else that I should be doing?

thanks in advance.

---

### Post by Waappu on 2010-04-02
Hi,

Can you login to SQL plus as system user?


You can try change system user password.
Open terminal and type
```

sqlplus '/as sysdba'

```

Then in SQL plus
```

ALTER USER system ACCOUNT UNLOCK;
ALTER USER system IDENTIFIED by newpasswd;

```

Where newpasswd is password you like set for system user

---

