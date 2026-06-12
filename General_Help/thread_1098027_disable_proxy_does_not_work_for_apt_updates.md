---
title: "disable proxy does not work for apt updates"
date: 2009-03-16
forum: General Help
---

### Post by bogdanbiv on 2009-03-16
I had setup my system proxy (System->Preferences->Network Proxy) to work at school on my laptop. After I filled in the school_proxy_ip and school_proxy_port for http, https and ftp I had clicked 'apply system wide'

The problem is that when I connect from home, where I don't have a proxy, even if I choose 'direct internet connection' and 'apply system wide', when it looks for packages to update/install it spits out this error:
> 
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.0.20.4-0ubuntu2.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.0.20.4-0ubuntu2.1_all.deb)
  403 Forbidden [IP: school_proxy_ip 8080]

When I ping the school's proxy from home it responds with the same ip as in the error (that is how I found the root of the problem).
 
Here's what happens when I try other http clients
> laptop:~$ wget google.com
--2009-03-16 21:54:08--  [http://google.com/](http://google.com/)
Resolving school_proxy_DNSname... school_proxy_ipAddress
Connecting to school_proxy_DNSname|school_proxy_ipAddress|:8080... connected.
Proxy request sent, awaiting response... 403 Forbidden
2009-03-16 21:54:08 ERROR 403: Forbidden.


Firefox works fine, but the rest seems broken. Do you please have any ideas?
system info: > 
Ubuntu 8.10, 64 bit
Linux bogdanbiv-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
laptop:~$ cat /proc/version
Linux version 2.6.27-11-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:28:32 UTC 2009

---

### Post by LegendofTom on 2009-03-16
When you get home, run ```
/etc/init.d/networking restart
``` and then run update.

---

### Post by Sverre J on 2009-04-27
Shameless bump, I have the same problem, and the fix mentioned above does not seem to help. I get the 
```
 * Reconfiguring network interfaces...                                   [ OK ] 

```But to no avail.

---

### Post by BenniP on 2009-05-23
similar thread:
[http://ubuntuforums.org/showthread.php?t=1064343](http://ubuntuforums.org/showthread.php?t=1064343)

Workaround:

type in the console:

http_proxy=
https_proxy=

---

