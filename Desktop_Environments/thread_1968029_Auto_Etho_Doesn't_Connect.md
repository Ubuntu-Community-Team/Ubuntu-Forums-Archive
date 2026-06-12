---
title: "Auto Etho Doesn't Connect"
date: 2012-04-28
forum: Desktop Environments
---

### Post by vigs on 2012-04-28
The motherboard of my laptop was recently replaced, due to a overheating issue. After the replacement, I'm unable to connect through the wired ethernet in my room on Ubuntu. I dual boot with Windows, and the wired ethernet works perfectly there, so it is not a hardware problem. I currently use Gnome 3 - it may be worth noting that I've always controlled the Network Settings through Gnome's network Manager interface.

I suspect that the problem is that it's still trying to connect using the old MAC address - however, I'm not sure. How to troubleshoot this problem and how to fix it?

---

### Post by Perryg on 2012-04-28
MAC address changes in Linux forces a new eth* but you can either edit the "/etc/udev/rules.d/70-persistent-net.rules" or you can delete the rules and Linux will configure it on the next boot.

---

