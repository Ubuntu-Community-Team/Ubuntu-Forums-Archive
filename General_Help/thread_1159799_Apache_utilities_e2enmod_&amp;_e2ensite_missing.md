---
title: "Apache utilities e2enmod &amp; e2ensite missing"
date: 2009-05-15
forum: General Help
---

### Post by slipstream180 on 2009-05-15
Hi all - I am using the desktop version of 9.04. I am trying to set up Apache for SSL. However, as the Apache Doc page ([https://help.ubuntu.com/9.04/serverguide/C/httpd.html](https://help.ubuntu.com/9.04/serverguide/C/httpd.html)) recommends using the e2enmod & e2ensite to facilitate configuration, I can't seem to find it on my machine...

I've tried:
> find -name e2enmod

from root & it comes up empty. (Just in case it's sitting outside my path somewhere)

I've also tried 
> sudo apt-get upgrade apache2-common 

which comes back with something about apache2-common being deprecated to apache2.2.-common. If I try apache2.2.-common it says there's nothing to update.

Scanning the standard search engines seems to come up empty for these two binaries...

Any ideas as to how to get these helpful utilities, or some apt-get commands to debug our way to a full installation?

Thanks in advance, for any ideas/help.

Cheers.

---

### Post by slipstream180 on 2009-05-15
Problem solved. It's not e2enmod. It's **a**2enmod.

---

