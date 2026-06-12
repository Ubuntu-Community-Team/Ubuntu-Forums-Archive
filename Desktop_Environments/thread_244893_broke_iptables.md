---
title: "broke iptables"
date: 2006-08-27
forum: Desktop Environments
---

### Post by Nikusan on 2006-08-27
Hey all,

After forwarding the required ports for ekiga and also putting my computer in my router's DMZ, ekiga was still reporting Symmetric NAT.

So I decided to run the script located [in their FAQ]("http://www.gnomemeeting.org/index.php?rub=3&pos=0&faqpage=x161.html#AEN163")... Now I can't get on the network. Can someone help me undo this mess?

---

### Post by stdragon on 2006-08-28
You can try:

iptables -F INPUT
iptables -F OUTPUT
iptables -F FORWARD
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT

If that doesn't work I'd reset your router.

---

### Post by Nikusan on 2006-08-28
That worked, thanks :D

---

