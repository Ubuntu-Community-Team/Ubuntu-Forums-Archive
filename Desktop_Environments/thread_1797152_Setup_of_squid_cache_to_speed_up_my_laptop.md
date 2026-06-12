---
title: "Setup of squid cache to speed up my laptop"
date: 2011-07-04
forum: Desktop Environments
---

### Post by jflinux on 2011-07-04
So I keep 200 webpages open.
It takes forever to load all those webpages on 3Mbps DSL.
So I want to run squid cache on my laptop.

So I installed Squid cache.
Question1 :  Which is the squid.conf I am using?
# locate squid.conf
/etc/init/squid.conf
/etc/squid/squid.conf
/etc/squid/squid.conf.original
/usr/share/doc/squid/examples/squid.conf
/var/lib/dpkg/info/squid.conffiles
/var/lib/dpkg/info/squid.config
# ps auxww | egrep squid
root      1666  0.0  0.0  22036   560 ?        Ss   11:48   0:00 /usr/sbin/squid -D
proxy     1668  0.0  0.3  37940 18644 ?        S    11:48   0:07 (squid) -D
root      5562  0.0  0.0   8952   868 pts/0    S+   14:35   0:00 egrep squid

I want to modify the squid.conf, but there are many to chose???

Question2: Where is the squid cache directory?
If found it doing locate:  /var/spool/squid
Most recent files seem to be going here: /var/spool/squid/00/0F

Question3:  Why does the /var/log/squid/access.log have this over and over?
1309804455.603      0 127.0.0.1 TCP_NEGATIVE_HIT/500 294 GET [http://img.tweetimag.es/i/danielpmaloney](http://img.tweetimag.es/i/danielpmaloney) - NONE/- text/html
1309804455.606      0 127.0.0.1 TCP_NEGATIVE_HIT/500 294 GET [http://img.tweetimag.es/i/danielpmaloney](http://img.tweetimag.es/i/danielpmaloney) - NONE/- text/html
1309804455.609      0 127.0.0.1 TCP_NEGATIVE_HIT/500 294 GET [http://img.tweetimag.es/i/danielpmaloney](http://img.tweetimag.es/i/danielpmaloney) - NONE/- text/html
1309804455.612      0 127.0.0.1 TCP_NEGATIVE_HIT/500 294 GET [http://img.tweetimag.es/i/danielpmaloney](http://img.tweetimag.es/i/danielpmaloney) - NONE/- text/html
...   repeats the above hundreds or more times.

Question4:   Is there an environment variable to tell all browsers: opera, firefox, chromium
to use 127.0.0.1:3128 ?   what line do I type in which file to set it?

Ok. I have it configured and running manually changing all my browsers to point at the proxy 127.0.0.1 port 3128 .
However, no speed improvement and a slight bit more swapping due to squid using some memory.
Looks like squid has zero benefit since the browsers have cache which does the same job.

Thanks!!

---

