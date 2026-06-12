---
title: "Apache2 status"
date: 2009-01-18
forum: Desktop Environments
---

### Post by MatsB on 2009-01-18
I keep getting this error from my PC which have 192.168.0.10: You don't have permission to access /server-status on this server

This is how i configure it on my server 192.168.0.2 /etc/apache/apache2.conf:


ExtendedStatus On
<Location /server-status>
    SetHandler server-status
    Order Deny,Allow
    Deny from all
    Allow from  192.168.0.10
</Location>

I've reloaded apache ofc:


/etc/init.d/apache2 reload

Any ideas?

---

