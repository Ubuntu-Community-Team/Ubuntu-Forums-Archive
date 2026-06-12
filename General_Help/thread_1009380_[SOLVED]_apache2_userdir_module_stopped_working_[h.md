---
title: "[SOLVED] apache2 userdir module stopped working [hardy]"
date: 2008-12-12
forum: General Help
---

### Post by david@artefactual.com on 2008-12-12
I've been using the userdir module with Apache2 on Hardy Heron for 8 months without problem - but it suddenly stopped working this morning.  The only thing that I can think of that may have caused it to stop working is that I ran the "Update Manager" yesterday and installed a bunch of updates - including some to the php binaries (I'm not sure if it also updated apache).

I tried:

```

~$ sudo a2enmod userdir
This module is already enabled!

```

And restarted apache just to make sure userdir didn't get turned off somehow.  The conf files show up as expected in /etc/apache2/mods-enabled:

```
~$ ls -l /etc/apache2/mods-enabled/userdir*
lrwxrwxrwx 1 root root 30 2008-12-12 11:13 /etc/apache2/mods-enabled/userdir.conf -> ../mods-available/userdir.conf
lrwxrwxrwx 1 root root 30 2008-12-12 11:13 /etc/apache2/mods-enabled/userdir.load -> ../mods-available/userdir.load

```

To test the current apache user I created a simple php file:

[PHP]<?php echo `whoami` ?>[/PHP]

which returns "www-data" (from the url: [http://localhost/~david/myname.php](http://localhost/~david/myname.php)) instead of my user "david".

I searched around for posts about this problem but I haven't found anything helpful.  If I knew how to find a roll-back the updates from yesterday I would give that a try.

Any help is appreciated.

Regards,
David Juhasz

---

### Post by david@artefactual.com on 2008-12-12
Turns out that update manager installed libapache2-mod-php5 which doesn't play nicely with the userdir mod. :)

Uninstalled libapache2-mod-php5 and restart apache and everybody is happy again.

David

---

### Post by rrll1977 on 2009-05-18
Hi all,

Has anybody got to work mod_rewrite with mod_userdir

I can't get mod_rewrite to work with user's pages on /home/user/public_html, although it appears to work fine for server root pages on /opt/lampp/htdocs

Regards

---

