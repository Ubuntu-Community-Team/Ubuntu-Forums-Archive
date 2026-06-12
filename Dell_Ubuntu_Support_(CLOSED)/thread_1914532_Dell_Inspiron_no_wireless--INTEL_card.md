---
title: "Dell Inspiron no wireless--INTEL card"
date: 2012-01-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by notacompwiz on 2012-01-24
Help! I'm having trouble connecting to wireless, especially during heavy-usage times (evenings).  I've looked through other threads posted but apparently my Dell Inspiron N4110 has an intel wireless card (the other threads discuss Broadcom cards). I tried the sudo get update but the wireless is still patchy. Any suggestions?


~$ lspci -nn | grep 0280
01:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [8086:008a] (rev 34)

~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [8086:008a] (rev 34)
Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
Kernel driver in use: iwlagn
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
Subsystem: Dell Device [1028:04d7]
Kernel driver in use: r8169

---

### Post by pythonsyntax on 2012-03-24
i got the same wireless card not sure how to get it to work in linux.

---

### Post by UltimateCat on 2012-03-24
These 2 websites can help with drivers to help your r8169 that is already in use.

[http://www.driverupdate.net]("http://www.driverupdate.net/")

[http://www.official-drivers.com/inst...FYNo4AodQ3dXxw]("http://www.official-drivers.com/installer/?seed=realtek&gclid=CP-NqNLI5a4CFYNo4AodQ3dXxw")

I see you have the RTL8101E.....I have the RTL8168 and had to blacklist the r8169 for my system to be able to go online.  I used the driver to help me. You will have to look for the driver that is compatible for your network interface card.

After installing the driver I rebooted....you should also

Hope this helps

---

### Post by pythonsyntax on 2012-03-27
Try the dell tool come with ubuntu that slove the prob it did help me.

---

