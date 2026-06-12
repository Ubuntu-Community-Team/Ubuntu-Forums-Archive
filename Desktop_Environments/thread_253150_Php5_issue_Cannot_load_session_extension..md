---
title: "Php5 issue: Cannot load session extension."
date: 2006-09-07
forum: Desktop Environments
---

### Post by zazery on 2006-09-07
Recently I upgraded all my packages and didn't notice that php was being upgraded from php4 to php5. Now when I go to my phpmyadmin setup it give me the following error:

```
Cannot load session extension. Please check your PHP configuration.

```

I have tried to find the session module and it appears that it is installed with php4. In my php.ini file there is no extension=session.so. What package must I install for the session module to be installed?

Thanks

---

### Post by marianom on 2006-09-07
Hi, see if this helps:
[http://ar.php.net/manual/en/ref.session.php](http://ar.php.net/manual/en/ref.session.php)

Additionally I suggest checking in the phpinfo the Configure Command to verify all required options are enables although the php docs says you don't need to enable any extension but there's several options mentioned there.

---

