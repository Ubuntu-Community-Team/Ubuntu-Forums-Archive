---
title: "konqueror works, but firefox doesn't"
date: 2006-02-18
forum: Desktop Environments
---

### Post by tiodan on 2006-02-18
working on a new install of kubuntu here, and i've installed firefox since that's what i've always used on previous systems. funny thing is, firefox can't seem to find the internet. konqueror and kopete work just fine (i'm writing this in konqueror), but firefox just times out every time. i feel like i must be missing something here. any ideas?

---

### Post by cwaldbieser on 2006-02-18
[QUOTE=tiodan]working on a new install of kubuntu here, and i've installed firefox since that's what i've always used on previous systems. funny thing is, firefox can't seem to find the internet. konqueror and kopete work just fine (i'm writing this in konqueror), but firefox just times out every time. i feel like i must be missing something here. any ideas?[/QUOTE]
In the Firefox URL bar, enter "about: config".  Filter on the "network.dns.disableIPv6" setting.  If it is set to false, try setting it to true.

Other than that, are you using a proxy?

---

