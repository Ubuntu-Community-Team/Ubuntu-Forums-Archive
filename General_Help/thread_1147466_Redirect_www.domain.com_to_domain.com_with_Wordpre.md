---
title: "Redirect www.domain.com to domain.com with Wordpress"
date: 2009-05-03
forum: General Help
---

### Post by benuski on 2009-05-03
Hi everybody,

I've just created a Wordpress site on my home server.  When I had a Drupal site on it before, I was able to use the ServerAlias field to have domain.com and [www.domain.com](www.domain.com) both show the same thing.  However, with Wordpress I now get a 404 with [www.domain.com](www.domain.com) and the proper website with domain.com.  How do I get it so both work?

Thanks in advance!

---

### Post by bodhi.zazen on 2009-05-03
[http://pushkararora.com/how-to/how-to-redirect-your-domaincom-to-wwwyour-domaincom/](http://pushkararora.com/how-to/how-to-redirect-your-domaincom-to-wwwyour-domaincom/)

Put those into your apache config file rather then .htaccess

---

### Post by benuski on 2009-05-03
Now when I go to [www.domain.com](www.domain.com), instead of getting a 404 error, firefox tries to download a PHTML file, which seems to be the index.php of my wordpress installation. I can also browse the file structure of my document root through [www.domain.com](www.domain.com), but can't see the website normally through it. But how can I just get it to display instead of trying to download? It works fine on domain.com...

And it happens without the rewrite code enabled as well.

---

### Post by benuski on 2009-05-03
Oh, I figured it out.  And it was really really easy.

On the server, I just had to run sudo ln -s /etc/wordpress/config-domain.com.php /etc/wordpress/config-www.domain.com.php

Now [www.domain.com](www.domain.com) redirects to domain.com. No redirect codes needed.

---

