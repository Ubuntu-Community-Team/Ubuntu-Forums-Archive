---
title: "Apache2 and DNS stuff"
date: 2009-04-15
forum: General Help
---

### Post by jonny75904 on 2009-04-15
Hi all,

I recently installed Apach2, MySQL, and PHP5 so I could locally install and test Joomla.  Since I have done that my computer now takes 3-5 seconds to find any web page (even google).

My guess is my computer now looks to itself for DNS resolution and times out, then uses the ISP's DNS.  

I would like to be able to configure my machine so that when I'm doing development work I can browse my local sites, but when I'm done developing I can flip a switch to make access quick again (my wife hates the slow browsing time).

---

### Post by JochenJung on 2009-04-16
Have a look at /etc/resolv.conf
This file determines where your PC looks for name resolution

---

