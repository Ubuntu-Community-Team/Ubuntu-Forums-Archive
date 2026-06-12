---
title: "php5-gd works on apache2, but doesn't work on nginx"
date: 2009-05-18
forum: General Help
---

### Post by digitalred on 2009-05-18
Hi.

I installed nginx, php5, apache2, php5-gd, ...etc. using apt-get or aptitude install, somehow gd isn't enabled on nginx, but it's enabled and working perfectly on apache2. 

/etc/php5/cgi/conf.d does have gd.ini with the line ```
extension=gd.so 
```I can't figure out what's missing for nginx, any idea or suggestion?

---

problem solved... system reboot was required... probably to restart fastcgi?

---

