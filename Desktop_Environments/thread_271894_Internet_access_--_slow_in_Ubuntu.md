---
title: "Internet access -- slow in Ubuntu"
date: 2006-10-05
forum: Desktop Environments
---

### Post by astral69 on 2006-10-05
Accessing the internet is painfully slow in Ubuntu.
Back to Windows it is fast.
Same line, same router/modem settings all saved in the router.
Any ideas.

---

### Post by Kateikyoushi on 2006-10-05
Try to check what nameservers you use in linux and windows.
In linux it is in etc/resolv.conf

---

### Post by pstewart on 2006-10-05
I take it you're using Firefox, yes?

If so, try entering about:config in the address bar and filter ipv6. You should see an entry "network.dns.disableIPv6", set this to "true" and it should force Firefox to use IPv4 and speed things up a bit.

Hope that helps,
Pete

---

### Post by johnmce on 2006-10-21
thanks a lot disabling ipv6 solved my slow internet as well.:D

---

### Post by Kateikyoushi on 2006-10-21
I have a question, does synaptic work for you ?
Noticed some people with IPV6 could make FF work but not synaptic.

---

### Post by stansaraczewski on 2006-10-22
Thank You PSTEWART ! Disabled ipv6 and my performance improved.

I love this forum.

---

### Post by epq on 2006-10-27
Thanks
Ive been trying to solve this problem for ages.
Disabling ipv6 worked a treat!

---

### Post by Ramses de Norre on 2006-10-27
Check also [this](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4) and [this](http://www.ubuntuforums.org/showthread.php?t=179540).

---

