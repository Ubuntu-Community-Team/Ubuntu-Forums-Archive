---
title: "Bootup Time / Bootchart"
date: 2009-01-20
forum: General Help
---

### Post by Rezzie on 2009-01-20
I have Ubuntu 8.04 installed on my netbook and would like get the boot time down a bit as it currently takes much longer than the default Xandros install (66s for Ubuntu vs. ~30s for Xandros).

I have installed bootchart and ended up with /var/log/bootchart.tgz, but no rendered image and the web renderer at the homepage seems to be down (using either a browser or curl). I cannot render them locally (running "java -jar bootchart.jar" gives a Main-Class error, and "java -cp bootchart.jar org.bootchart.Main" also gives an error).

Firstly, is there any way to render my boot log, either locally or using a web service. Secondly, could someone please look at my bootchart and tell me how to save a bit of time? I have already reprofiled and disabled unneeded services and startup programs.

Thanks in advance.

---

### Post by EricS on 2009-01-29
There is a form at the very bottom of this page:
[http://www.bootchart.org/download.html](http://www.bootchart.org/download.html)

---

