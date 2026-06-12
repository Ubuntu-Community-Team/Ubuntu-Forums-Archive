---
title: "Stealthing ports"
date: 2009-03-31
forum: General Help
---

### Post by Nithrin on 2009-03-31
How do I stealth my ports. A lot of firewalls allow you to go into stealth mode. What do I need to do this in Ubuntu and how do I do it? Also, how do I hide what I view on the internet? I don't want to surf and have others be able to see what I am viewing if I can help it.

---

### Post by HermanAB on 2009-03-31
It pointless to do that.

---

### Post by Nithrin on 2009-03-31
Why is it pointless to stealth my ports or try and hide my internet trail?

---

### Post by bodhi.zazen on 2009-03-31
stealthing ports = drop

closed = reject

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

You can not be invisible when connected to the internet. You can use tor which will help , but has limits. For example I do not think you can log in to any banking site over tor (https) or use cookies for example.

---

### Post by Nithrin on 2009-03-31
Does this mean I should not even bother using Firestarter or iptables at all?

---

### Post by stderr on 2009-03-31
No, it's a good idea to use something like that (I use UFW, with the gufw package) to configure iptables to close all ports aside from those you specifically want to be open.

As for not letting others see what you're doing... well... not easy. As bodhi mentioned, there are networks such as tor, but really in terms of day-to-day use, it's more about ensuring if you're on a wireless network, it's encrypted, and that when you enter sensitive information online (such as a password) it's using SSL encryption (typically it uses the prefix https:// to indicate SSL traffic on port 443).

But there are still many, many ways of getting around these security measures, such as man-in-the-middle attacks, arp poisoning etc.

Bottom line: follow basic internet security advice, and using something like you mentioned (firestarter, gufw, ...) to configure iptables would be good. Also, if you have additional web-based services enabled such as SSH, extra steps can typically be taken (such as denyhosts).

---

### Post by phantom3113 on 2009-03-31
I have heard that the newest release of Firefox (vs. 3.1; currently in Beta) has an option that you can use called "private browsing" or something similar. From what I saw/read, it puts you into a browsing mode where it doesn't record your browsing history or things of that nature. As to browsing invisibly, that's generally impossible as far as I know

---

### Post by redsoxreed on 2009-03-31
Proxy server anyone?

---

### Post by dcstar on 2009-03-31
> **phantom3113 said:**
> I have heard that the newest release of Firefox (vs. 3.1; currently in Beta) has an option that you can use called "private browsing" or something similar. From what I saw/read, it puts you into a browsing mode where it doesn't record your browsing history or things of that nature.

The Stealther add-on does this now.

---

