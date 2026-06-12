---
title: "Cross Site Scripting"
date: 2009-03-10
forum: General Help
---

### Post by CrusaderAD on 2009-03-10
Does anyone know if there's a utility for Ubuntu that scans IPs for cross site scripting vulnerabilities? Or maybe one that scans local servers?

---

### Post by edu1962 on 2009-03-11
> **raptormanad said:**
> Does anyone know if there's a utility for Ubuntu that scans IPs for cross site scripting vulnerabilities? Or maybe one that scans local servers?

Firefox NoScript - extention does this and much more ! :D

---

### Post by CrusaderAD on 2009-03-12
Oh yeah. I knew about that, but it only scans the page you're on right? What if there are 1000's of pages? That's why I need a scanner program.

---

### Post by CrusaderAD on 2009-03-19
Bump!

---

### Post by CrusaderAD on 2009-08-04
Bump!

---

### Post by CrusaderAD on 2009-08-05
Acunetix Does this, but it's only Windows and super expensive. Their free edition is borderline useless.

[http://www.acunetix.com/cross-site-scripting/scanner.htm]("http://www.acunetix.com/cross-site-scripting/scanner.htm")

---

### Post by CrusaderAD on 2009-08-12
Paros Proxy works great. It scans and generates an html report. Wapiti is pretty good too.

[http://www.parosproxy.org]("http://www.parosproxy.org")

---

### Post by doas777 on 2009-08-12
check this out:
[http://www.gnucitizen.org/blog/javascript-xss-scanner/](http://www.gnucitizen.org/blog/javascript-xss-scanner/)

I've used the free version of acunetix on a few apps. never turned up anything, but makes me feel better.

---

### Post by CrusaderAD on 2009-08-13
> **doas777 said:**
> check this out:
[http://www.gnucitizen.org/blog/javascript-xss-scanner/](http://www.gnucitizen.org/blog/javascript-xss-scanner/)

I've used the free version of acunetix on a few apps. never turned up anything, but makes me feel better.

That's cool. Do you know of anything that scans the source code and gives you results / solutions?

---

### Post by doas777 on 2009-08-13
XSS exploits are as much about configuration as code, so I'm not sure an offline code scanner could turn it up anyway. acunetix does provide some reports, but never tried any of the others. 
my guess is you still have to give it a server to crawl.

---

### Post by CrusaderAD on 2009-08-14
These guys had a nice list of software to use. Some in java, some in Python. Good stuff.

[http://0x0e.org/drupal/?q=node/6]("http://0x0e.org/drupal/?q=node/6")

---

