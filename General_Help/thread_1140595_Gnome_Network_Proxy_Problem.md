---
title: "Gnome Network Proxy Problem"
date: 2009-04-27
forum: General Help
---

### Post by mr_skater99 on 2009-04-27
Hi Guys,

Here's my issue.  

Did a complete fresh install of 9.04 yesterday.  Set up Gnome Network Proxy and Authentication for it.

Working fine - when i 'export $http_proxy' i get [http://user:pass@proxy:port/](http://user:pass@proxy:port/)

Problem is after a restart only [http://proxy:port/](http://proxy:port/) is being exported - the auth is missing.

And so most things fail with a 407 from the proxy.  The auth credentials are still set and correct - is there a bug with gnome proxy?

I thought about setting this in a global bashrc (as its needed always for this desktop) but i have a lot of exclusions i need for the proxy.

Is there a way to manually set this globally and also set proxy exceptions?

Cheers.

---

