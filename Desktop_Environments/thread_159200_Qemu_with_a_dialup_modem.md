---
title: "Qemu with a dialup modem"
date: 2006-04-12
forum: Desktop Environments
---

### Post by frag79 on 2006-04-12
I have a dialup serial modem and cannot get an internet connection to work with qemu. I've tried installing ubuntu, suse, and freebsd in qemu and I can't dial up in any of them so I assume it is a qemu problem. 

Thanks

---

### Post by towsonu2003 on 2006-04-14
I'm not sure I understand. So let's say you are running Ubuntu. and Suse is running in Qemu. In this case:

Dial up with ubuntu, set up Suse to use eth0 with dhcp for networking. the eth0 Suse will be using is independent of your ethernet card. it's just an emulated hardware used by qemu to bridge the emulated OS and the real OS' network. 

If you're using the most up-to-date qemu (compiled by yourself), you won't have to give any options while starting qemu for networking. if it's ubuntu's qemu,you might wanna check out the qemu man page and try combinations of the options given there (or similar).

---

