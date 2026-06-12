---
title: "How ask idle DSL connections to stay connected?"
date: 2006-01-13
forum: General Help
---

### Post by K_Dallas on 2006-01-13
Hi!

Ubuntu-breezy. DSL connction is set (pppoeconfig) and seems to be working just fine except that if an application (browser, irc, ...) idles for a few min, that application is disconnected from outside even though the other active ones remains connected.

Where should and what parameter should I change to make it connected all the time?

Thanks in advance!

---

### Post by Mr_Grieves on 2006-01-13
So.. what you're saying is, if you for example have two IRC clients up (eg. two connections) and one of the clients idle for a time, it's disconnected?

If so.. it seems that this is not a problem with you're DSL connecting being idle, but a problem with you're TCP/IP communication.

Do you use a router/switch that you connect you're computer to? If so, try and connected you're computer directly to you're DSL modem and see what happens.

---

### Post by K_Dallas on 2006-01-13
That is exactly the case.

1. If i connect thru the router, the connection remains on as long as I want.

2. The problem occurs when I connect to the modem directly.

Thanks for your attention.

PS: Same system on Windows offers no problem neither with router nor without.

---

