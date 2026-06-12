---
title: "How to remove non-working volume controller in Indicator plugin?"
date: 2013-10-29
forum: Desktop Environments
---

### Post by jeandre2 on 2013-10-29
The Notification area suddenly has the Sound output volume, which it didn't on my previous boot (update?). 

The problem is that I don't know how to get rid of the other volume controller in the Indicator plugin (which hasn't worked since installing a clean Xubuntu 13.10 (that same volume controller worked fine on my clean Xubuntu 13.04)), and I don't even know what it's called so I can uninstall it because the Indicator plugin has no options UI either from a context click, nor in Panel preferences, Items tab, Edit button. 

I don't want to uninstall the Indicator plugin because I want the network indicator in it.

---

### Post by Yellow Pasque on 2013-10-31
You can make it work again:

[https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1208204/comments/5](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1208204/comments/5)

---

### Post by jeandre2 on 2013-11-01
Thanks Temüjin for the link to fix indicator-sound-service.   Others in the same situation can get rid of (instead of just hiding) the working Sound output volume by going to Settings manager, Sessions and startup, Application autostart, and disabling Volume control.

---

