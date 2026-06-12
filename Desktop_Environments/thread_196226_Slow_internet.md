---
title: "Slow internet"
date: 2006-06-13
forum: Desktop Environments
---

### Post by vasimakhtar on 2006-06-13
Hi
After installation of Automatix, my PC is working slow and also internet access. Is it something related to space in my PC or this is in general.
thanks

---

### Post by adwait on 2006-06-13
Depends. When you enter an address in the browser, does it take a long time to look it up? If so, you need to turn off ipv6. In firefox type
```
about:config
```

in the address bar. Search for a key called ipv6disable and set it to true. That should speed up your browsing. You can turn ipv6 entire pff by editing the /etc/modprobe/aliases file. Search on the forum for exact details, I don't remember them off the top of my head. :)

---

