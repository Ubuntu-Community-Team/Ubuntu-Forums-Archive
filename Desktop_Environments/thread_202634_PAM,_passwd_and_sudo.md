---
title: "PAM, passwd and sudo"
date: 2006-06-23
forum: Desktop Environments
---

### Post by myyst on 2006-06-23
Hi!

I`m trying to specify minimal password length using PAM. 
Let`s look at default /etc/pam.d/common-password

```

password   required   pam_unix.so nullok obscure min=4 max=8 md5

```

So minimal length is 4. When I change the password of currently logged user

```
myst@zephir:~$ passwd
```

everything is ok. I can`t pass password shorter then 4 characters.
However just try to change password of other user using sudo

```
myst@zephir:~$ sudo passwd test
```

Now one even passowrd shorter then 4 characters is accepted.
Does sudo omits PAM rules?

So maybe try to login as root

```

myst@zephir:~$ sudo su -
root@localhost:~# passwd test

```

Unfortunetly too short passwords are accepted again.
Am I doing something wrong? 
Maybe root can pass any-length passwords.
In that case how to specify that no-one, event root, can pass passwords shorter then some number of characters?

Thanks in advance.

---

