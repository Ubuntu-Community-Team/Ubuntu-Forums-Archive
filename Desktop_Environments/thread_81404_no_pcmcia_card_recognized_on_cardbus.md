---
title: "no pcmcia card recognized on cardbus"
date: 2005-10-24
forum: Desktop Environments
---

### Post by kai.springer on 2005-10-24
Hi guys,

I got a problem with my cardbus. When I’m plugging in either my D-Link DWL G650+ or my Belkin Wireless Lan Card into the pcmcia bus, nothing happens. When I type Cardctl status it says no card. Iwconfig doesn’t show any interface apart from lo,  eth0 or sit0. Installing the original driver with ndiswrapper doesn't change anything either. As I can’t find anything further about that on the internet I hope you can help me. I got a Benq Joybook R22E and tried that with Kubuntu 5.10. In Windows XP it works properly, so I think my hardware is fine.

Thanks for your help in advance

Kai

---

### Post by cus on 2005-10-24
I had this problem on kernels prior to 2.6.13  - have you *ever* had working pcmcia on linux kernels prior to this?

The good news is that 2.6.13 has rebuilt PCMCIA capabilities and I've been able to get pcmcia cards up and running on my laptop with no hassle at all with that kernel. I'm away from my machine at the moment, but it's an ICH6-based centrino laptop.

I was able to recompile the 2.6.13 kernel from kernel.org with no problems and it works without a hitch now.

---

### Post by kai.springer on 2005-10-24
Well, it's my first laptop and so it's the first time I got that problem. I had Kubuntu Hoary working on my PC before and haven't changed anything at a Kernel since.

---

