---
title: "How to re-install apache2?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by claytonc on 2006-06-03
Hi,

I've been  trying to remove apache2 using the command - ```
sudo aptitude remove apache2
```. When I try to re install the package using the command ```
sudo aptitude install apache2
```, it doesn't re write all the files, such as apache2.conf and the default web page doesn't appear in the browser. All in need to do is to remove and re install a fresh copy of apache2! Can somebody help me pls?

Thanks,
Clayton

---

### Post by harisund on 2006-06-03
sudo aptitude purge apache2-common
sudo aptitude install apache2

---

### Post by claytonc on 2006-06-04
Ok thanks, it worked

---

