---
title: "apt-cacher error"
date: 2009-05-25
forum: General Help
---

### Post by geraldvillorente on 2009-05-25
> 
root@wizardsides:~/Desktop# /etc/init.d/apt-cacher-ng start
 * Starting apt-cacher-ng apt-cacher-ng                                         Couldn't bind socket: Address already in use
Couldn't bind socket: Address already in use
No socket(s) could be create/prepared. Check the network, check or unset the BindAddress directive.
                                                                         [fail]


Anyone who can shed me some light?

---

### Post by geraldvillorente on 2009-05-25
Bump!

---

### Post by ad_267 on 2009-05-25
Check this guide: [http://ubuntuforums.org/showthread.php?t=564301](http://ubuntuforums.org/showthread.php?t=564301)

Make sure you have these lines in /etc/services if you're using the daemon mode:
```
apt-cacher           3142/tcp
apt-cacher           3142/udp
```
(Assuming that's the port you want to use)

---

### Post by geraldvillorente on 2009-05-25
Tnx Sir.

---

