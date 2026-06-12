---
title: "Is apache2-mpm-prefork a prerequisite for phpmyadmin?"
date: 2009-05-10
forum: General Help
---

### Post by rexeast on 2009-05-10
Hi,

I have apache2 installed, and am using mpm-worker instead of mpm-prefork for my website. I would like to install phpmyadmin. When I do "apt-get install phpmyadmin", I get the following message:

```
The following extra packages will be installed:
  apache2-mpm-prefork [...and some other stuff]

The following packages will be REMOVED:
  apache2-mpm-worker
```

Is there a workaround for this so that I don't have to uninstall apache2-mpm-worker?

Thanks!

---

### Post by surplusxmas on 2009-08-20
I have the same question.

---

