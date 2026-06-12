---
title: "Unable to search Forum!"
date: 2018-04-05
forum: Forum Feedback &amp; Help
---

### Post by rsteinmetz70112 on 2018-04-05
I logged in and attempted a seatc and get:

```
Forbidden
You don't have permission to access /search.php on this server.

Apache/2.4.7 (Ubuntu) Server at ubuntuforums.org Port 443
```

Search phrase was:

```
 Unknown Multi-Arch type '#same' for package 'libkf5coreaddons5'
```

---

### Post by coffeecat on 2018-04-05
So do I.

The firewall rules that Canonical IS instituted a couple of years ago are sometimes triggered by certain strings or phrases. Try simplifying your search phrase. Taking out '#same' allows a search and includes this thread. That may or my not help you, but try fine-tuning your search phrase.

---

### Post by rsteinmetz70112 on 2018-04-05
Thanks. It appears the the '#" was causing the problem.  I wonder why those rules were instituted inside the forums.

---

### Post by coffeecat on 2018-04-05
> **rsteinmetz70112 said:**
> I wonder why those rules were instituted inside the forums.

A very serious security breach by malicious hackers.

---

