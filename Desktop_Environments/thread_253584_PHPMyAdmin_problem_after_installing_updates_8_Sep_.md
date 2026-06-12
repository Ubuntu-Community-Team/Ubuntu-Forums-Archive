---
title: "PHPMyAdmin problem after installing updates 8 Sep 2006"
date: 2006-09-08
forum: Desktop Environments
---

### Post by serpentskiss on 2006-09-08
Hi All

After installing the updates this morning (loads of php/mysql ones), I found that I couldn't display anything in phpmyadmin. It was taking too much time trying to fix, so I uninstalled it, removed all the entries from the machine (as the uninstall doesn't), then reinstalled

Now I can run it, but I get 

```
Warning: include(/etc/phpmyadmin/config.header.inc.php) [function.include]: failed to open stream: No such file or directory in /usr/share/phpmyadmin/config.header.inc.php on line 6
Warning: include(/etc/phpmyadmin/config.footer.inc.php) [function.include]: failed to open stream: No such file or directory in /usr/share/phpmyadmin/config.footer.inc.php on line 6
```

at the top and bottom of each page. Simply copying/changing ownerships/permissions doesn't solve the issue - if I do that, then it treats a php file like a download.

I know from my previous install that these were in /etc/phpmyadmin/, but now all that's in there is 

blowfish_secret.inc.php
htpasswd.setup

Any hints/solutions??

Cheers

Jon

---

### Post by tturrisi on 2006-09-08
did you have a look at usr/share/phpmyadmin/config.header.inc.php on line 6 ?

---

### Post by serpentskiss on 2006-09-18
duh... yeh ;-)

That looks for the file named in theerror, that doesn't exist.

Get's better now. I can't even log in to phpmyadmin, even though i'm using the correct host/user/pass (checked via command line) and confirmed it using scripts/setup.php

---

