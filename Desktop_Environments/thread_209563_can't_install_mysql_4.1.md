---
title: "can't install mysql 4.1"
date: 2006-07-05
forum: Desktop Environments
---

### Post by harty83 on 2006-07-05
I need to install mysql-server4.1 for testing purposes because my web servers all still run mysql-4.1.  But when I go  to install the server, I get the following error:

```
E: /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb: subprocess pre-installation script returned error exit status 1
```

Can anyone help me?

Thanks!

---

### Post by bohboh on 2006-07-05
Try 

apt-get clean

and try again.

If it happens again then use aptitude, handles installations better.

---

### Post by harty83 on 2006-07-05
[QUOTE=bohboh]Try 

apt-get clean

and try again.

If it happens again then use aptitude, handles installations better.[/QUOTE]

I tried it again after running apt-get clean and the same thing happened.  So I did apt-get clean again then tried to install it with aptitude.  I got the same error.  Any other suggestions?

---

### Post by bohboh on 2006-07-05
Are there any other error messages? I got a similar problem once with another installation but i got another error message as well which helped me to fix it, can you post the entire installation output?

---

