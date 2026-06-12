---
title: "Remote Desktop does not work with windows."
date: 2009-05-03
forum: General Help
---

### Post by yogo on 2009-05-03
I can connect between all Ubuntu boxes with Desktop viewer but can not connect to a Windows laptop with VNC server running nor can I connect the Windows laptop to the Ubuntu boxes.

I also have tried Terminal Server Client but no success.

*I am using the right ip addy's but *nothing works.

Been reading everywhere but no ideas so far, help greatly appreciated.

---

### Post by Brandon Williams on 2009-05-03
It sounds like the Windows machine is not allowing the packets in or out. Do you have a firewall of some sort running on the Windows box? If so, you may have to change some settings in that software in order to enable communication on the desired port(s).

---

