---
title: "Apache / Ubuntu very slow to respond to web requests"
date: 2009-03-13
forum: General Help
---

### Post by yogi799 on 2009-03-13
I am on a local home network with Ubuntu machine running LAMP.

Most of the time when I access my web server on this machine from my other computers on the network it takes about 5 seconds to load up the first page. Subsequent pages load quickly until I take a 30-60 second break. Then again, first web request will take 5 seconds, and so on. 

At times it responds like a thunder to all requests - no problem. Recently however, it's been more often in the slow mode. This was not the case when I first installed Ubuntu/LAMP on this box. 

What could be the problem? My LAN speed is huge and the pages I request tiny. FTP seems to be working really fast, so is VNC and all others. Is this an Apache problem? How can I troubleshoot it (I tried restarting Apache, not the whole box, though). Where are the logs for Apache stored? Or any other ideas?

---

### Post by yogi799 on 2009-03-13
Anyone?

---

### Post by DGortze380 on 2009-03-13
It's typically consider rude to bump your thread before 24 hrs.

Have you tried accessing the page via the ip address rather than host name?

Sounds like a DNS / Host Name issue to me.
If this works, an easy solution would be to add your server name to /etc/hosts, or to run a local DNS Server on the LAMP.

---

### Post by yogi799 on 2009-03-14
> **DGortze380 said:**
> It's typically consider rude to bump your thread before 24 hrs.

Have you tried accessing the page via the ip address rather than host name?

Sounds like a DNS / Host Name issue to me.
If this works, an easy solution would be to add your server name to /etc/hosts, or to run a local DNS Server on the LAMP.


I am accessing the server via IP, 192.168.0.xxx.
Where should I add and what? 

I just tried something - on the LAMP server itself, when I call the site using localhost/... it brings it up immediately. Would this be an issue with my router and/or switch, then? I tried rebooting both...

Oh, and again - FTP for example is working with no delays when calling the same way, using IP 192.168...

---

### Post by DGortze380 on 2009-03-14
> **yogi799 said:**
> I am accessing the server via IP, 192.168.0.xxx.
Where should I add and what? 

I just tried something - on the LAMP server itself, when I call the site using localhost/... it brings it up immediately. Would this be an issue with my router and/or switch, then? I tried rebooting both...

Oh, and again - FTP for example is working with no delays when calling the same way, using IP 192.168...

I figured it would work, but...

 are web requests **faster** using the IP??

---

### Post by yogi799 on 2009-03-15
> **DGortze380 said:**
> I figured it would work, but...

 are web requests **faster** using the IP??

Faster than what? I have always used the IP to access my LAMP machine on my home LAN. First request takes 5-6 seconds, immediate subsequent ones are super fast.

---

