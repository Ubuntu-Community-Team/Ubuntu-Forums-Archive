---
title: "Home Server Security Question"
date: 2009-05-29
forum: General Help
---

### Post by jdavidw13 on 2009-05-29
Hey everyone,

I just had a quick question about security for my personal home webserver.  My server is meant to be accessible only to myself, and I plan to serve some php scripts which could be harmful to my system if other users had access to them (php file manager, php terminal emulator, etc.).  To secure this, I have enabled ssl on my apache instance, and created a .htaccess file with AuthType basic in the root directory where all these potential harmful php scripts will live (/var/www/private).  I should also mention I've given ownership of the /var/www/private directory to the apache user, www-data I believe.  

When I access my scripts, I use [https://mydomain/private](https://mydomain/private) and am prompted with a login dialog from apache.  My question then, will this provide adequate security as a personal home server?

---

### Post by jdavidw13 on 2009-08-25
Bump.  Would love to get an answer to this.

---

