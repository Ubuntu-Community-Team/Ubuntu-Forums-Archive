---
title: "Squid3 proxy unable to access ubuntuforums.org?"
date: 2012-12-15
forum: Forum Feedback &amp; Help
---

### Post by CyberAngel on 2012-12-15
I face an annoying and hard to track its root problem with squid3 proxy server running on Ubuntu Server 12.04.

Squid is working fine for all websites I have tried so far to access, except [http://ubuntuforums.org/](http://ubuntuforums.org/)

What I get is the following error:

```
ERROR

The requested URL could not be retrieved

The following error was encountered while trying to retrieve the URL:
http://ubuntuforums.org/

Access Denied.

Access control configuration prevents your request from being allowed
at this time. Please contact your service provider if you feel this is
incorrect.

Your cache administrator is webmaster.

```
Notice also that the cache administrator is **webmaster**, while I have changed the *cache_mgr* parameter in the squid.conf file with my own e-mail and for any other errors I see it properly.

In the access.log I see this every time I try to access the forums.

```
1355572568.095    217 192.168.0.10 TCP_MISS/403 4567 GET http://ubuntuforums.org/ - DIRECT/91.189.94.12 text/html
```

The bizarre thing here is that I can access sub paths of the forum like [http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php) or /newthread.php (that I use right now for this post over my proxy) without any problems!

I tried to purge the cache by using **squidclient** but again I get the following error:

```
# squidclient -m PURGE [http://ubuntuforums.org/](http://ubuntuforums.org/)
HTTP/1.0 404 Not Found
Server: squid/3.1.19
Mime-Version: 1.0
Date: Sat, 15 Dec 2012 12:14:48 GMT
Content-Length: 0
X-Cache: MISS from localhost
X-Cache-Lookup: NONE from localhost:3128
Via: 1.0 localhost (squid/3.1.19)
Connection: close
```

---

### Post by NickD-NLUG on 2013-01-01
I'm seeing the same thing, very weird ;)

Let me know if you've found an explanation, or a solution, or a workaround... if not I'll see what I can come up with...

---

### Post by CyberAngel on 2013-01-02
Haven't found anything yet :(

Please share if you do and happy new year by the way :)

---

### Post by awil on 2013-01-05
I get the same thing. I even tried to whitelist the site in the config file and restarted the service. I received the same error. Could it be blocked by ip address in the free black lists I downloaded? I'll have to research this later.

---

### Post by NickD-NLUG on 2013-01-14
> **awil said:**
> I get the same thing. I even tried to whitelist the site in the config file and restarted the service. I received the same error. Could it be blocked by ip address in the free black lists I downloaded? I'll have to research this later.

If the main page is blocked by a free blacklist all the pages underneath it should be blocked too, and the FQDN will remain the same.

Meanwhile, it *appears* to be working for me now... maybe it was related to this issue: [http://ubuntuforums.org/showthread.php?t=2091969](http://ubuntuforums.org/showthread.php?t=2091969) ?

---

### Post by CyberAngel on 2013-01-14
Working for me as well now.

> **NickD-NLUG said:**
> If the main page is blocked by a free blacklist all the pages underneath it should be blocked too, and the FQDN will remain the same.

Meanwhile, it *appears* to be working for me now... maybe it was related to this issue: [http://ubuntuforums.org/showthread.php?t=2091969](http://ubuntuforums.org/showthread.php?t=2091969) ?

---

### Post by awil on 2013-01-17
It works after I white listed the site. I grep the ip and the website and didn't find it in the blacklist.

---

