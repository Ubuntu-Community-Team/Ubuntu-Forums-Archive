---
title: "Proxy Issue with ActiveGrid Application"
date: 2009-06-01
forum: General Help
---

### Post by LookUpSeeBlu on 2009-06-01
Hi,

I have a linux server that is running an activegrid application that calls a webservice.  We recently moved the proxy server to a new IP address and whenever I call this webservice, it is trying to go out to through the old proxy settings (seen by doing a netstat -a).  I have exported $http_proxy and even done a grep -rIl 'OLD_IP' and changed any of the corresponding files.  It seemed to be fixed when I exported the http_proxy variable but then stopped working and started going out to the old proxy IP a few days later (suddenly).  Neither TUX nor Squid are running or doing any webcaching.  The server runs tomcat and activegrid.  The line from netstat -a is:

tcp    0     0     ORIG_IP    OLD_PROXY_IP:webcache     SYN_SENT

How can I get rid of this?  This is a very important server and I need to get it going ASAP.

Thank you more than you can know for any help.

Kevin

---

### Post by LookUpSeeBlu on 2009-06-01
Also, ActiveGrid is written in Python, so how can I check and see what proxy urllib2 is using?

Thanks.

Kevin

---

