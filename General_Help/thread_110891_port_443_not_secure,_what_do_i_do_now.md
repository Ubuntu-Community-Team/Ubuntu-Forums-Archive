---
title: "port 443 not secure, what do i do now ?"
date: 2005-12-31
forum: General Help
---

### Post by dage on 2005-12-31
Hi all,
I've tested my firewall (firestarter) at [www.hackerwatch.org](www.hackerwatch.org) and all my port (list in the web) is secure especially the 443 port: 
> Closed but Unsecure
443 (HTTPS)

This port is not being blocked, but there is no program currently accepting connections on this port.

Is this port is important ? If yes, what i gotta do to secure it ?
 Thanks ;)

---

### Post by Svictor on 2005-12-31
Not an expert myself, but I would say it isn't important. https is the "secured" version of http. So you want it open while you browse the internet, as you want the http port itself (port 80 as far as I know) to be opened. The test probably doesn't report anything about port 80 being opened (it obviously is since you can see the web page of the test). But I think 443 is not a problem neither.
As I said, I'm not an expert but I remember having wondered the same thing after a port-scan test. That was one year ago, and nothing nasty happened since (actually, since I switched to Linux, nothing nasty happened at all ; I'm using firestarter as well).

---

### Post by dage on 2006-01-01
thanks a lot and happy new year (bonne ann&#233;e) ;)

---

