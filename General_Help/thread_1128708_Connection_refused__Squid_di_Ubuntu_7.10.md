---
title: "Connection refused : Squid di Ubuntu 7.10"
date: 2009-04-17
forum: General Help
---

### Post by xmbohx on 2009-04-17
i configured squid in ubuntu 7.10, using ip address 10.6.1.1
the squid.conf seemed like this :

```

http_port 3128

icp_port 0

visible_hostname proxy
acl QUERY urlpath_regex cgi-bin \?

no_cache deny QUERY

cache_mem 8 MB

cache_dir ufs /chace 4500 16 256

redirect_rewrites_host_header off

acl localnet src 10.6.1.0/24

acl localhost src 127.0.0.1/255.255.255.255

acl pcku src 10.6.1.100
acl Safe_ports port 80 443 210 119 70 21 1025-65535

acl CONNECT method CONNECT

cache_mgr me@localhost

cache_access_log /var/log/squid/access.log

cache_store_log /var/logs/store.log

cache_log /var/logs/cache.log

log_icp_queries off

cachemgr_passwd hehehehe
acl manager proto cache_object

http_access allow manager

acl all src 0.0.0.0/0.0.0.0

http_access allow localnet

http_access allow localhost

http_access allow pcku
http_access deny all


```

on pcku machine (client), configured like this
ip address : 10.6.1.100
subnet mask : 255.255.255.0
gateway : 10.6.1.1
dns : 10.6.1.1

and the firefox browser configured like this : 10.6.1.1, port: 3128

when browse to any url, eg. [www.yahoo.com](www.yahoo.com), the browser showed error message : connection refused

fyi, i can remote the ubuntu machine 10.6.1.1 using putty/ssh

pls help

---

