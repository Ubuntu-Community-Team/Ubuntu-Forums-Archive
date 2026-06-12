---
title: "Got an IP, but no internet"
date: 2009-05-12
forum: General Help
---

### Post by CrusaderAD on 2009-05-12
I have a ubuntu server setup with a static ip address. I can browse it just fine on the local network, but it has no outside connection. I can't browse the net on the server. Other machines with a static ip run the net with no issues. Any ideas?

---

### Post by prem1er on 2009-05-12
Can you ssh in or out of the box from outside your LAN?

---

### Post by CrusaderAD on 2009-05-12
I got it. I had the static ip set, but not the dns.

```
sudo vi /etc/resolv.conf
```

---

