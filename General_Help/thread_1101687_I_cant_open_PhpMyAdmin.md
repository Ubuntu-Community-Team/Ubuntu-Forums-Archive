---
title: "I cant open PhpMyAdmin"
date: 2009-03-20
forum: General Help
---

### Post by DizzyEwok on 2009-03-20
Hi,
I have installed and configured MySQL on my Ubuntu 8.10 laptop, and I have also installed phpMyAdmin via apt-get. 
Many sites are telling me to go to localhost/phpMyAdmin to run it. But when I go to it in firefox, it just says:
```
Not Found

The requested URL /phpmyadmin was not found on this server.
Apache/2.2.8 (Ubuntu) Server at localhost Port 80
```

Any Ideas on how I can get it working?

Thanks in advance!

---

### Post by LoneWolfJack on 2009-03-20
keep in mind linux is generally case-sensitive... ;-)

---

### Post by dyingsun on 2009-03-25
It could be having a spit if you didn't include the trailing slash on the end of the URL. I think its all supposed to be in lowercase.
Try this:

```
http://localhost/phpmyadmin/
```




Can you see a subdirectory in /usr/share called phpmyadmin?
If not, it may not be installed properly.

---

