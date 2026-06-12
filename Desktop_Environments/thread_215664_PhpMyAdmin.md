---
title: "PhpMyAdmin"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Aurdal on 2006-07-14
So, finally I've got my developement server up and running. Or, I thought so... You see, PhpMyAdmin complains about requiring a blowfish_secret (strangely enough it worked yesterday)...

```
Error
The configuration file now needs a secret passphrase (blowfish_secret).
```

Now. I can't recall having changed anything since it worked. So, can anyone please help me out here?


Also, MySQL Administrator keeps freexing whenever I try to go to the "user administration" tab.

Thanks. :)
-Aurdal

---

### Post by lurchi on 2006-07-14
:-)

[http://www.apachefriends.org/f/viewtopic.php?t=14750&](http://www.apachefriends.org/f/viewtopic.php?t=14750&)

---

### Post by Aurdal on 2006-07-14
Thanks, how ever the blowfish thingy in /etc/phpmyadmin is included in the config file, and the installation automatically generated a phrase to put in it.

```
// Load secret generated on postinst
include('/etc/phpmyadmin/blowfish_secret.inc.php');
```
^Lines 7 and 8 from /var/www/phpmyadmin/config.inc.php

EDIT: The Windows Way prevailed. :s Rebooting fixed the whole thing. :D

-Aurdal

---

### Post by eeried on 2006-07-17
Restarting mysql and apache2 should have done the trick -- forget  M$ ways!

---

### Post by Aurdal on 2006-07-19
You see, I tried that, I even tried reinatalling the both of them...

---

