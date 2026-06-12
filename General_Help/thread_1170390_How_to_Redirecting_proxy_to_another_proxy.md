---
title: "How to: Redirecting proxy to another proxy?"
date: 2009-05-26
forum: General Help
---

### Post by rufia on 2009-05-26
My problem goes like this:

Our Company need to access a web-based version of a specific program.  Unfortunately our proxy server, to which we connect at our HQ, does not have enough bandwidth to process all the user request to the specific web address.

We have one IP that has access to the Internet via the backbone of the ISP.  So what we did was to setup our own Squid proxy to which the PCs can connect via a Web browser, but now we need to redirect all the traffic via our own proxy to the proxy of the ISP.  This should happen on the same server.

How do I do this?  We use Ubuntu 8.10 and Squid 3.

---

### Post by upbeat.linux on 2009-05-26
You can find helpful hints here:

[http://wiki.squid-cache.org/SquidFaq/ConfiguringSquid](http://wiki.squid-cache.org/SquidFaq/ConfiguringSquid)

See these two sections:

* How do I configure Squid to work behind a firewall?
* How do I configure Squid forward all requests to another proxy?

Also, this sounds like something that could be more efficiently handled on your router, switch, or firewall (see WCCP).

---

### Post by rufia on 2009-05-27
Thanks, I will look into this and maybe also speak to our ISP to see if we can do this on the router.

---

