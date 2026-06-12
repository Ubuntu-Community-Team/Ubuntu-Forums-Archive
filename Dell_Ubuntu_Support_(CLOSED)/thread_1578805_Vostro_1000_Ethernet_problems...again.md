---
title: "Vostro 1000 Ethernet problems...again"
date: 2010-09-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by d_fiumano on 2010-09-21
Heyo! I'm having problems with my ethernet again. Sometimes it will connect when I turn my computer on, but it usually does not and I have to input this in the terminal  to get it up & running again: [service network-manager stop]
                         [service network-manager start]

Once again, any help would be greatly appreciated.

---

### Post by jaakan on 2010-09-21
Did you do a clean install?
Did it happen after you updated the kernel?
What happens when you use a live CD of 10.04 x64 or 10.10 x64?

---

### Post by d_fiumano on 2010-09-21
I did a clean install. I installed 10.04 X64 right over 9.14 X32. As for the Kernel, I think so. As for the live cd, haven't tried that; not too sure if it would make a difference. I'm a few steps higher than a noob, but I'm still learning this OS.

---

### Post by jaakan on 2010-09-21
> **d_fiumano said:**
> I did a clean install. I installed 10.04 X64 right over 9.14 X32. As for the Kernel, I think so. As for the live cd, haven't tried that; not too sure if it would make a difference. I'm a few steps higher than a noob, but I'm still learning this OS.

I have that same laptop. I have noticed that when a new kernel comes out I sometimes have to reboot twice to get a network connection via wireless, reboots after that are just fine. A live CD is great way to test your hardware, I use the Startup Disk Creator (usb-creator-gtk) to make a boot disc on a flash drive so I don't waste CDRs. 

What changes have you made related to networking?

if your using dhcp on your network, Ethernet should just work booting from a live CD, U8.10 and newer.

---

### Post by d_fiumano on 2010-09-26
I haven't changed anything. I have it set to automatic, but sometimes when I power on, the wifi overrides the LAN & I have to deactivate & reactivate in the terminal.

---

