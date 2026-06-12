---
title: "Open Relay in Apache."
date: 2010-03-11
forum: Desktop Environments
---

### Post by khatkarrohit on 2010-03-11
Yesterday I installed Apache server on my computer having Ubuntu9.10 Desktop amd64 version.

I find this line in apache logs:

118.160.208.213 - - [11/Mar/2010:13:17:32 +0530] "CONNECT maild.agc.idv.tw:25 HTTP/1.0" 405 559 "-" "-"

I searched it on net and find it is something related to spammers and spammers are trying to use my server.
**I foud this on internet:-**
> >CONNECT 195.***.76.123:25 
>Can someone explain to me what this person is trying to do?
Since port 25 (smtp) has been hit, it's likely a spammer trying to use your server as a spam relay server.

The Limit rule shoud block 'em.

>Would this still be written to the log files though?

Afaik yes. But with a 403 status code instead of 200.

btw, Welcome to WebmasterWorld [webmasterworld.com], DrTebi. :)"



Are spammers successful with it.

**Router Settings:**
I have enabled DMZ in my router for my PC.
NAT -- Virtual Servers - I am using http and ftp server.
No ports are forwarded.

so all ports are blocked except 80 and 21.
then how a spammer get a hit at 25 port.

Please explain it.

---

### Post by lisati on 2010-03-11
Apache doesn't use port 25, it uses port 80. Isn't the 405 an error code?

---

### Post by khatkarrohit on 2010-03-26
Please explain what these persons from these ip's trying to do.

217.195.122.125 - - [24/Mar/2010:10:07:13 +0530] "CONNECT 217.195.122.125:6667 HTTP/1.0" 405 560 "-" "-"
217.195.122.125 - - [24/Mar/2010:10:07:41 +0530] "POST [http://217.195.122.125:6667/](http://217.195.122.125:6667/) HTTP/1.0" 200 4317 "-" "-"
217.195.122.125 - - [24/Mar/2010:10:08:10 +0530] "PUT [http://217.195.122.125:6667/](http://217.195.122.125:6667/) HTTP/1.0" 405 556 "-" "-"
118.161.249.26 - - [24/Mar/2010:15:22:50 +0530] "CONNECT maild.agc.idv.tw:25 HTTP/1.0" 405 559 "-" "-"
91.212.127.100 - - [25/Mar/2010:05:37:14 +0530] "GET [http://ant.dsabuse.com/abc.php?auth=45V456b09m&strPassword=PSTHTVGYCCDJA&nLoginId=43](http://ant.dsabuse.com/abc.php?auth=45V456b09m&strPassword=PSTHTVGYCCDJA&nLoginId=43) HTTP/1.1" 404 465 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.0; en-US; rv:1.8.1.12) Gecko/20080201 Firefox/2.0.0.12"
118.161.242.172 - - [25/Mar/2010:06:29:02 +0530] "CONNECT maila.agc.idv.tw:25 HTTP/1.0" 405 559 "-" "-"
117.206.176.39 - - [25/Mar/2010:14:15:47 +0530] "GET / HTTP/1.1" 200 4355 "-" "EZI_HTTP_NETDEV_DISCOVER"
118.168.135.89 - - [26/Mar/2010:00:29:19 +0530] "CONNECT mail3.xps.idv.tw:25 HTTP/1.0" 405 559 "-" "-"
118.168.135.89 - - [26/Mar/2010:01:45:10 +0530] "CONNECT mail3.xps.idv.tw:25 HTTP/1.0" 405 559 "-" "-"
118.168.135.89 - - [26/Mar/2010:03:00:54 +0530] "CONNECT mail3.xps.idv.tw:25 HTTP/1.0" 405 559 "-" "-"
118.168.135.89 - - [26/Mar/2010:04:16:41 +0530] "CONNECT mail3.xps.idv.tw:25 HTTP/1.0" 405 559 "-" "-"
188.105.18.56 - - [26/Mar/2010:04:40:24 +0530] "GET [http://httpproxylist.org/cgi-bin/my_jenv.pl?a=80&b=117.206.176.2](http://httpproxylist.org/cgi-bin/my_jenv.pl?a=80&b=117.206.176.2) HTTP/1.0" 404 502 "-" "Mozilla/4.0 (compatible; MSIE 5.5; Windows NT 4.0)"
118.161.248.97 - - [26/Mar/2010:04:51:10 +0530] "CONNECT maila.agc.idv.tw:25 HTTP/1.0" 405 559 "-" "-"
118.168.135.89 - - [26/Mar/2010:05:34:00 +0530] "CONNECT mail3.xps.idv.tw:25 HTTP/1.0" 405 559 "-" "-"
118.168.135.89 - - [26/Mar/2010:06:49:54 +0530] "CONNECT mail3.xps.idv.tw:25 HTTP/1.0" 405 559 "-" "-"
118.168.135.89 - - [26/Mar/2010:08:05:42 +0530] "CONNECT mail3.xps.idv.tw:25 HTTP/1.0" 405 559 "-" "-"
217.195.122.126 - - [26/Mar/2010:08:33:08 +0530] "CONNECT 217.195.122.126:6667 HTTP/1.0" 405 560 "-" "-"
217.195.122.126 - - [26/Mar/2010:08:33:35 +0530] "POST [http://217.195.122.126:6667/](http://217.195.122.126:6667/) HTTP/1.0" 200 4317 "-" "-"
217.195.122.126 - - [26/Mar/2010:08:34:05 +0530] "PUT [http://217.195.122.126:6667/](http://217.195.122.126:6667/) HTTP/1.0" 405 556 "-" "-"
118.168.135.89 - - [26/Mar/2010:09:21:28 +0530] "CONNECT mail3.xps.idv.tw:25 HTTP/1.0" 405 559 "-" "-"
118.168.135.89 - - [26/Mar/2010:10:38:16 +0530] "CONNECT mail3.xps.idv.tw:25 HTTP/1.0" 405 559 "-" "-"
117.206.176.50 - - [26/Mar/2010:11:06:06 +0530] "GET / HTTP/1.1" 200 4355 "-" "EZI_HTTP_NETDEV_DISCOVER"
117.206.176.50 - - [26/Mar/2010:12:17:30 +0530] "GET / HTTP/1.1" 200 4355 "-" "EZI_HTTP_NETDEV_DISCOVER"
118.168.135.89 - - [26/Mar/2010:12:37:37 +0530] "CONNECT mail3.xps.idv.tw:25 HTTP/1.0" 405 559 "-" "-"
117.206.176.3 - - [26/Mar/2010:16:32:25 +0530] "GET / HTTP/1.1" 200 4355 "-" "EZI_HTTP_NETDEV_DISCOVER"

---

### Post by Nandox7 on 2010-03-26
Any machine directly exposed to the internet will receive connections
from all over the place.
If you plan to keep it like tthat you might consider installing a 
intrusion detection software.
Something like Snort or PortSentry, still always keep an eye on the logs for
any suspicious activity.

---

### Post by efflandt on 2010-03-28
405 error means "Method not allowed".  Crackers are attempting to see if you are running an open proxy on apache, but they were unsuccessful.

---

### Post by khatkarrohit on 2010-09-07
thanks everybody now i understand how things work on internet.

---

