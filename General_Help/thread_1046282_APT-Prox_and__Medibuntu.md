---
title: "APT-Prox and  Medibuntu"
date: 2009-01-21
forum: General Help
---

### Post by klab1 on 2009-01-21
Hi All

I am trying to setup apt-proxy to work with Medibuntu.  As it is configured now, when a client runs “aptitude update” using the proxy it just sits there at “0% [Waiting for headers]”.  

apt-proxy-v2.conf

[medibuntu]
;; Ubuntu medibuntu
backends = [http://packages.medibuntu.org](http://packages.medibuntu.org)
min_refresh_delay = 15m

I have also tried it with 

[medibuntu]
;; Ubuntu medibuntu
backends = [http://packages.medibuntu.org/hardy](http://packages.medibuntu.org/hardy)
min_refresh_delay = 15m


The client setup:
deb [http://proxy.server:9999/medibuntu](http://proxy.server:9999/medibuntu) hardy free non-free


Any help would be appreciated
Thanks

---

