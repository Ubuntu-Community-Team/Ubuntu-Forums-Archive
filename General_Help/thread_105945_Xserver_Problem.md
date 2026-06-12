---
title: "Xserver Problem?"
date: 2005-12-19
forum: General Help
---

### Post by derekho55 on 2005-12-19
Hi, I just installed Kubuntu 5.10 on my Sony Vaio B series laptop (VGN-B100B). Everything is very smooth. I was actually really surprised that the networking capabilities are really good in Kubuntu. 

I tried:
sudo kuser
and it works.

However, I tried to do access "kuser" while in su mode:

It states..
XLib: connection to "0.0" refused by server
XLib: No protocol specified

Kuser: Cannot connect to X server: 0.0

What do I need to configure in order to make this work?

Thanks.

---

### Post by jferrando on 2005-12-19
Try
$ **kdesu kuser**

And type your user (sudo-enabled) password...

---

