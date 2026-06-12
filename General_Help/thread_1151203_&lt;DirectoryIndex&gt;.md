---
title: "&lt;DirectoryIndex&gt;"
date: 2009-05-06
forum: General Help
---

### Post by vallarta on 2009-05-06
Hi guys I need to enable index.php but I can't find the <DirectoryIndex> can some please help me. Im using Ubuntu Hardy.

Thank you!

:KS:KS:KS:)

---

### Post by mb_webguy on 2009-05-06
Not sure what you're asking...  "Enable" index.php?  If you have PHP installed with Apache or another web server, "enabling" a PHP script is simply a matter of putting it in the web root directory.  In Apache, the default web root is the /var/www directory.  This owned by root, so unless you change permissions on this directory, you'll need to use sudo to access it.

---

