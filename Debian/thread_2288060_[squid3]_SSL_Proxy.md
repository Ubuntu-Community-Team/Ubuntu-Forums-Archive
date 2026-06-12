---
title: "[squid3] SSL Proxy"
date: 2015-07-24
forum: Debian
---

### Post by helpman2 on 2015-07-24
Hello, I would like to ask that
I want to have the function like this:
client"---(HTTPS)---"proxy"---(HTTP)---"actual web server"
and actual web server doesn't use SSL protocol.

The OS is Debian 8 and the proxy version is squid 3.4.8
Here is my configuration:

https_port 192.168.1.1:8124 transparent ssl-bump cert=/etc/squid3/server.crt key=/etc/squid3/server.key
cache_peer 192.168.1.21 parent 80 0 no-query originserver login=PASS name=websiteA
http_access allow all

But I got the error in /var/log/squid3/cache.log
kid1| clientNegotiateSSL: Error negotiating SSL connection on FD 10: error:1407609B:SSL routines:SSL23_GET_CLIENT_HELLO:https proxy request (1/-1)

How can I resolve it ?

Thanks everyone.

---

### Post by TheFu on 2015-07-24
What you need is called a "reverse proxy" - most people setup TLS (SSL is dead) termination using nginx or apache running in TLS termination mode.  Of course, as a client-side user, this is outside your control - only the people running the servers can do this.

For nginx, I can help. [https://www.nginx.com/resources/admin-guide/reverse-proxy/](https://www.nginx.com/resources/admin-guide/reverse-proxy/) and [https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)

Also be aware that not all reverse proxies support TLS termination. There are other limitations, like 1 IP = 1 TLS termination for a server using non-recent clients. This is a client-side limitation with name-based TLS virtual web domains.

---

### Post by TheDreamer on 2015-07-24
It has been a while, since I used squid & SSL, but when I did, the standard squid package wasn't compiled with SSL support so I had fetch the source and build my own package.

Here's my blog post related to this: [http://lawrencechen.net/2010/ddclient-aamp-squid](http://lawrencechen.net/2010/ddclient-aamp-squid) (which I've referred back to pretty much every time that I've needed to update the package ;)

The Dreamer.

---

