---
title: "PHPMyAdmin asks for passphrase"
date: 2006-03-10
forum: Desktop Environments
---

### Post by Ferio on 2006-03-10
Hi, I've just setup a LAMP server at home following the guidelines in [https://wiki.ubuntu.com/ApacheMySQLPHP]("https://wiki.ubuntu.com/ApacheMySQLPHP"); after solving some problems (I think I've solved them, at least) with MySQL passwords, I've installed PHPMyAdmin to manage it, but when I go to [http://localhost/phpmyadmin/index.php]("http://localhost/phpmyadmin/index.php"), it says > The configuration file now needs a secret passphrase (blowfish_secret).
I've found some tutorials on configuring PHPMyAdmin under Debian Sarge, but although it seems to be properly setup, it doesn't work and goes on telling me that I need this passphrase.

This is the first time that I setup a LAMP server and maybe I've forgotten something, though I don't think so. Could anybody help me, please? Thanks in advance!

PS: I've installed everything using Synaptic, and the only thing I've done different than the Wiki is installing MySQL 4.1 instead of 4.0, and PHP 5 instead of 4. I'm using Ubuntu repositories (normal, backports, security and updates), and main, restricted, universe and multiverse branches.

---

### Post by astyanax on 2006-03-10
Does it allow you to set a password?

If I'm not mistake, PHPMyAdmin is linked directly to MySQL.  If you login as root on PHPMyAdmin, you are logging on with root privileges for MySQL.

By default, MySQL installs with no password.  You can change the password by doing the following:
```
mysqladmin --user=root password "NEW_PASSWORD"
```

where NEW_PASSWORD is your new password.

That might fix your problem.

---

### Post by Ferio on 2006-03-11
I've found the solution. MySQL passwords were properly set, and Sarge's tutorial stated that /usr/share/phpmyadmin/config.inc.php should be configured, but this file said that you should modify /etc/phpmyadmin/config.inc.php instead. So, I've edited this file, adding> $cfg['blowfish_secret'] = 'The_Secret_And_Amazing_Passphrase'; and uncommenting the line which says > $cfg['Servers'][$i]['auth_type'] = 'cookie'; // Authentication method (config, http or cookie based)? Now everything works like a charm. Another battle won, thanks!

---

### Post by todd on 2006-03-11
You rock.  I just ran into this issue and really had no idea how to fix it.
Thanks.

---

### Post by bradlis7 on 2006-04-03
It would be nice if a PHPMyAdmin tutorial were in the wiki. Any volunteers?? :)

---

### Post by got_nix on 2006-05-03
you know this lil problem is gonna make me tear my hair out. now matter what i do it doens't work, i already had a blowfish_secret pass set auth_type is cookie it just stopped working.. i honestly dont get it

---

### Post by got_nix on 2006-05-03
i just solved it, i'm not sure why i had to deviate from the configuration layout that phpmyadmin was using from its default apt-get install, (not really sure why the config was layed out like that either) comment out the include of the blowfish_password.inc.php and put the content of the blowfish_password.inc.php in the config file located in the /etc/phpmyadmin/ dir

---

### Post by Railsbuntu on 2008-01-24
> put the content of the blowfish_password.inc.php in the config file located in the **/etc/phpmyadmin**/ dir

It's an old thread but it took me 1 hr to figure this out, most of the docs on the net don't talk about /etc/phpmyadmin.

---

