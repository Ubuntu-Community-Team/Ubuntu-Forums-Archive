---
title: "BIND9 selecting a prefered zone for hostname lookups help"
date: 2009-06-04
forum: General Help
---

### Post by syadnom on 2009-06-04
I have a BIND9 ubuntu 8.04 system that is working quite well.  I have just one issue that I dont know how to phrase properly to google.

I have BIND9 with 3 zones.  If I do lookups against the local DNS by host.domain.com everything works perfectly.

My issue is that I have a host in zone 1 ( drupal ) and a host on zone 2 ( drupal ).  If I lookup the hostname 'drupal' with either nslookup or dig or my web browser it pulls the record from zone 2 consistantly.  How can I set zone 1 as the prefered zone??

---

