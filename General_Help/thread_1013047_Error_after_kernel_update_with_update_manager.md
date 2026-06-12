---
title: "Error after kernel update with update manager"
date: 2008-12-16
forum: General Help
---

### Post by lsutiger on 2008-12-16
I updated the kernel to the latest for 8.04, along with a lot of other updates. Now I am receiving a notification (A yellow triangle with an exclamation point) in the notification area. 

When I hover over it I get a message to click and click on check. It open the Update manager.
When I click on check I get this error:
```
Failed to fetch http://mirror.ubuntulinux.nl/dists/hardy-seveas/freenx/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://mirror.ubuntulinux.nl/dists/hardy-seveas/freenx/source/Sources.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

Are these servers down or no longer used?

---

### Post by taurus on 2008-12-16
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and try another server.  Don't forget to click the Reload button.

---

### Post by lsutiger on 2008-12-16
Thanx for the reply....but what other servers?

Are those servers still in use? a 404 is pretty bad, considering :)

---

