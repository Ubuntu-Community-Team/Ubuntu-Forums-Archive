---
title: "Ubuntu Server 8.10 (LAMP inst): PHP5 not working"
date: 2009-02-15
forum: General Help
---

### Post by IslayMist on 2009-02-15
Hi,
I just installed Ubuntu Server 8.10, LAMP.
Everything seems to work perfectly well, except that PHP-code will not be parsed, or at least does not show in any browser, on any client.
I tried to verify various config options and they all seem fine and all according to instructions ( default config that is ). Nothing has been changed from installation settings.

For example, a file named index.html, isn't it possible to just verify the PHP-installation by adding "phpinfo();" ?

---

### Post by cb951303 on 2009-02-15
> **IslayMist said:**
> Hi,
I just installed Ubuntu Server 8.10, LAMP.
Everything seems to work perfectly well, except that PHP-code will not be parsed, or at least does not show in any browser, on any client.
I tried to verify various config options and they all seem fine and all according to instructions ( default config that is ). Nothing has been changed from installation settings.

For example, a file named index.html, isn't it possible to just verify the PHP-installation by adding "phpinfo();" ?

What's the result of opening an **index.php** file with the content of **<?php phpinfo(); ?>** ??

---

### Post by IslayMist on 2009-02-15
Yay ! :)
That did it, alright ! Thank you cb951303. So simple, yet so effective :)

---

