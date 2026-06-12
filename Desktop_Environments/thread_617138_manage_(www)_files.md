---
title: "manage (/www) files"
date: 2007-11-19
forum: Desktop Environments
---

### Post by sin_bad on 2007-11-19
Hi All
I want to manage (/www) files in ubuntu using desktop (KDE)  , like copy move delete extract .....
but every time I do so , I faced (Access denied) 
how to work as an administrator , with out going to command screen and use sudo 

Thank You

---

### Post by Thyme on 2007-11-19
Hi sin_bad,

Try changing the permissions for the folder that you want to put your web docs in. Something like:

My folder: /var/www/htdocs/website

sudo chown -R sin_bad /var/www/htdocs/website
chmod -R 0775 /var/www/htdocs/website

Hope this helps!

---

### Post by sin_bad on 2007-11-19
Thank you Thyme

I think doing so  will cause a security hole (in server environment) , isn't it  ???

---

### Post by Thyme on 2007-11-19
Yes I agree with you sin_bad.

You can try giving yourself read, write and execution permissions and everyone else read only permission:

```

chmod -R 0744 /var/www/htdocs/website

```

You can also create a group for people who need to work with the website and need write permissions to the folders:

My group: webdocs

```

chgrp -R webdocs /var/www/htdocs/website

```

And add write permission for that group

```

chmod -R g+w /var/www/htdocs/website

```

If you are running apache with a username that is not the owner or group of the directory, then you must have read permission for everyone else. You can change this in the apache.conf file.

Hope this helps:)

---

