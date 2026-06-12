---
title: "apache2 documentroot problem"
date: 2008-12-07
forum: General Help
---

### Post by wwuster on 2008-12-07
I'm running 8.10 desktop and have a problem with apache2. I have several local websites in /var/www. They have been working fine. I am now trying to set up one that would be in /home/user/_user/php as the documentroot. I've tried quite a few things in the
/etc/apache2/sites-available/testsite. Basically I have set documentroot to /home/user/_user/php and I have an index.html there. I ran a2ensite and restarted apache2. I also added testsite to /etc/hosts. I tried accessing the new index.html but I get the one in /var/www. Also I tried the testsite: localhost/testsite and I get "not found". This testsite is located in /home/user/_user/php/testsite and has an index.php.

Can you have some sites under /var/www and another one in a different directory at the same time? Can someone explain how to get this working?

thanks,
William

---

