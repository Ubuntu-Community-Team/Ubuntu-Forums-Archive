---
title: "help with squid urgent plz help"
date: 2006-02-16
forum: Desktop Environments
---

### Post by kasemodz on 2006-02-16
Alright I'm almost finished setting up squid however when running it, it terminates abnormally. Here is the output when i do > /etc/init.d/squid restart
> Restarting proxy server: 2006/02/16 19:52:47| ACL name '192.168.15.101/255.255.255.0' not defined!
FATAL: Bungled squid.conf line 5: http_access allow 192.168.15.101/255.255.255.0Squid Cache (Version 2.5.STABLE10): Terminated abnormally.
squid.


Here is my config file.
> http_port 8080
cache_mem 16 MB
cache_dir ufs /home/admin/cache/ 200 16 256
redirect_rewrites_host_header off
http_access allow 192.168.15.101/255.255.255.0
cache_effective_user admin
cachemgr_passwd my-secret-pass all
buffered_logs on


I used this site as my howto and kind of tweaked it. [http://howtos.linux.com/guides/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/chap28sec232.shtml]("http://howtos.linux.com/guides/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/chap28sec232.shtml")

---

### Post by Mustard on 2006-02-16
> http_access allow 192.168.15.101/255.255.255.0

Is that a valid option for http_access allow?

Here is the link to the squid docs if you haven't seen them already.

[http://squid-docs.sourceforge.net/latest/html/book1.html](http://squid-docs.sourceforge.net/latest/html/book1.html)

---

### Post by kasemodz on 2006-02-16
um it seems to be. I don't see any difference between that code and the manual besides the ip address.
> http_access deny 10.0.1.0/255.255.255.0
http_access allow 10.0.0.0/255.0.0.0
icp_access allow 10.0.0.0/255.0.0.0

---

