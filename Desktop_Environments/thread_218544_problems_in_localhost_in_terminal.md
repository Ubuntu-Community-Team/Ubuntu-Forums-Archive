---
title: "problems in localhost in terminal"
date: 2006-07-18
forum: Desktop Environments
---

### Post by redwolf963 on 2006-07-18
When I use wget,I get error messages that say "Cannot connect to localhost:port 80"My firestarter firewall shows my localhost port as being port 631.How do I reconfigure to use loopback at port 631,or change to port 80?
I hope I don't come off sounding as linux dumb as I am.
Any help would be greatly appreciated.
                     Thanks again, Scott

---

### Post by svaucher on 2006-07-18
Disclaimer: I'm somewhat of a newbie as well

1/ 631 is your CUPS port (printing) which by default (I believe) offers a web administration interface there. Your firewall probably keeps 631 open for http connexions, but I doubt you're trying to download something off CUPS...

2/ wget is a network downloader (e.g. to download off the web using http). If you want to download from localhost, you need to install a web server (like apache httpd).

hth,
Stephane

---

