---
title: "Help Changing the Default User in Apache"
date: 2006-08-03
forum: Desktop Environments
---

### Post by icedcheese on 2006-08-03
Hi There

I was wondering if someone could help me with this step:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Titled: Edit Apache Configuration

I have managed to open my configation file no problem, and can restart apache, but I have no idea what to type and where to put my user name in so I can have permission to put files into the var/www/ folder.

Can anyone help?

Thanks
Michael

---

### Post by pablo13 on 2006-08-03
Hi, I guess this is just a premission issue. I think if you add yourself to the www-data group and then change permissions for /var/www you will be able to write in that directory without problem

So
sudo vi /etc/group
and and your user name behind the :

And next,
sudo chgrp www-data /var/www
sudo chmod g+ws /var/www

Hope this help.
Pablo

---

### Post by icedcheese on 2006-08-03
Hi Pablo

Thank you for that, that solved the problem.

Thanks for the great support!

Michael

---

