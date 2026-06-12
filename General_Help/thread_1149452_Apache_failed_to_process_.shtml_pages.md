---
title: "Apache failed to process .shtml pages"
date: 2009-05-05
forum: General Help
---

### Post by nruner on 2009-05-05
I have installed and configured Apache2 on an Ubuntu PC, now it can process .html, .htm and .php files. Now there is a web page in format .shtml, it's Server Side Includes (SSI), How could I configure Apache to make it know .shtml pages? Thanks for help!

---

### Post by NoReflex on 2009-05-05
I must have mod_include enabled in Apache.
Check [http://httpd.apache.org/docs/1.3/howto/ssi.html](http://httpd.apache.org/docs/1.3/howto/ssi.html)

Best wishes,
NoReflex

---

### Post by nruner on 2009-05-05
Thank you NoReflex.

Ubuntu has splitted httpd.conf into several files, it make the configuration a little more difficult. Who could give me some detailed info or configuration steps? Thanks!

---

### Post by nruner on 2009-05-06
Who could tell me how to configure it on Ubuntu? Thanks!

---

