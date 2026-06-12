---
title: "Can't add certificates to firefox"
date: 2009-01-20
forum: General Help
---

### Post by Kissell on 2009-01-20
I was using webmin a lot on my laptop, but ever since I upgraded it to Ubuntu Intrepid Ibex I can't use webmin anymore...  

When I go to any IP address or hostname of a server with webmin on it, I get asked to download the site certificate and confirm a security exception... except when I click CONFIRM SECURITY EXCEPTION nothing happens, the window doesn't close and its not accepted...  

Anyone know how I can get around this...  I really miss being able to use webmin inside firefox. 

PS: I attached a screenshot.

---

### Post by drs305 on 2009-01-20
My notes are a bit sketchy on this, but I remember I had problems adding any certificates. I think when I got to the point at which you provided the snapshot I had to add an exception. 

Edit, Prefs, Advanced, View Certificates, Servers, Add Exception. When the window appears with "https://" I had to add these:
services.addons.mozilla.org
addons.mozilla.org

After I put these two in it would accept other certificates.

---

### Post by Kissell on 2009-01-20
When I go into the certificates menu and try to add those two sites, it says there is no need to add them, they're already built-in.

But, I did notice on the authorities tab that webmin is an authority for other named servers I used to have, but not an authority for the named servers I'm trying to use it with now...  so I removed those entries for webmin from the authorities list, then purged webmin and re-installed it...  but no luck.

---

### Post by Kissell on 2009-01-20
I have no idea why I couldn't get it to work...  but eventually I just used 

> firefox -ProfileManager 

to create a new profile in firefox to use that cleared out all my old settings...  and now I can confirm the certificate exception.  So I guess problem solved.

Firefox must have gotten confused when i copied my home folder from the old ubuntu install into the new version (and changed my hostname in the process).  I think my profile wasn't able to trust myself anymore.  Although, I'm not sure why it didn't resolve this problem on its own, creating a new firefox profile seems to have fixed it.

---

