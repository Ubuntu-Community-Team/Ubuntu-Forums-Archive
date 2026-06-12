---
title: "LAMP issue on 8.10"
date: 2008-12-12
forum: General Help
---

### Post by russone on 2008-12-12
Hello

Not sure if this is the right place for this but...

Installed LAMP on 8.10 desktop.  All ok and phpinfo() returns correctly and phpmyadmin loads ok but when I try and show a project I'm working on localhost, I get the attached error.  It's probably something simple in the configs I've overlooked, any ideas?

Thanks.

---

### Post by redilyn on 2008-12-12
Did you install LAMP using tasksel?

Looks like a permission problem.

Check to see what user apache is running under and then make sure that user has permission to access /usr/share/php & /usr/share/pear

---

### Post by russone on 2008-12-13
Hi redilyn and thanks for your help.

Yes I installed it using tasksel.

The owner of /usr/share/apache2 is root.

/usr/share/pear and /usr/share/php don't exist.  There is a /usr/share/php5.  This directory owner was root but I chown'd it to me.  Still no joy.

Attached is a screenshot of php.ini (original with no changes) for include_path which is currently commented out.  If I uncomment it, and set it to /usr/share/php5 it still doesn't work even after: /usr/sbin/apache2ctl restart

Thanks.

---

### Post by redilyn on 2008-12-13
You say phpmyadmin works fine, so apache and php should be working fine.

Maybe try to load a basic php file from your webdir and see if it loads alright. something like 

<?php
print 'hello';
?>

If so, i think you will have to check the coding in the page your trying to open now.

---

