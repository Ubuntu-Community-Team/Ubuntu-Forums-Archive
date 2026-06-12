---
title: "Samba sharing; Can't enable sharing"
date: 2008-12-29
forum: General Help
---

### Post by willthebold on 2008-12-29
When I try to share a folder after selecting "Share this folder", I get the message: "'net usershare' returned error 255: net usershare add: failed to add share ad. Error was Operation not permitted." I've restarted, logged out and in, and completely removed Samba and reinstalled it. This is 8.10 Intrepid 32-bit.

---

### Post by Nepherte on 2008-12-29
You probably need root privileges. Try using "share this folder" from:
```
gksudo nautilus
```

---

