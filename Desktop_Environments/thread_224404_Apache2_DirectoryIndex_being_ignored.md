---
title: "Apache2 DirectoryIndex being ignored"
date: 2006-07-27
forum: Desktop Environments
---

### Post by djdennie on 2006-07-27
I'm trying to set up some named virtual hosts with one of them having DirectoryIndex set to 'librarian.php' (instead of the usual index.php).

FYI, I've got both 'lms.jericho.com' and 'lib.jericho.com' setup in my /etc/hosts file.

This is what my configuration looks like:

```
<Directory "/usr/share/php/data/symfony/web/sf">
  AllowOverride All
  Allow from All
</Directory>

NameVirtualHost *

<VirtualHost *>
  ServerName lms.jericho.com
  DocumentRoot "/home/dhotson/lms/web"
  DirectoryIndex index.php
  Alias /sf /usr/share/php/data/symfony/web/sf

  <Directory "/home/dhotson/lms/web">
    AllowOverride All
    Allow from All
  </Directory>
</VirtualHost>

<VirtualHost *>
  ServerName lib.jericho.com
  DocumentRoot "/home/dhotson/lms/web"
  DirectoryIndex librarian.php
  Alias /sf /usr/share/php/data/symfony/web/sf

  <Directory "/home/dhotson/lms/web">
    AllowOverride All
    Allow from All
  </Directory>
</VirtualHost>
```

The problem is that it seems to be ignoring the DirectoryIndex directive. When I visit [http://lms.jericho.com](http://lms.jericho.com) and [http://lib.jericho.com](http://lib.jericho.com) , they both go to index.php .

Any ideas?

---

### Post by Jhongy on 2006-07-27
Two things spring to mind... first of all, you can try deleting the <Directory> </Directory> part that is outside of the Virtualhost blocks.

The other thing is the possibility that Apache won't like it if the directories are the same (Dunno if this is the case)... in which case, you could overcome this by creating a symbolic link from lms/web directory to a "fake" directory, say /lms/web2, and pointing Apache to that.

---

### Post by djdennie on 2006-07-28
Ok.. the web2 symlink seems to fix the problem (On fedora at least.. I'll try my ubuntu when I get home).
But that's not really an ideal solution.. It feels like a hack. :S

It would be better if you could have two virtual hosts with the same DocumentRoot, but a different DirectoryIndex.

---

### Post by Jhongy on 2006-07-28
I dunno... isn't doing this kindof "hackish" in the first place?  ;-) Virtualhosts normally point to different file paths.

---

### Post by djdennie on 2006-07-28
It will have do for now.. :)

Thanks for your help. I really appreciate it!

---

