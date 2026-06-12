---
title: "Wireless &amp; video drivers on 64bit 1501"
date: 2007-06-24
forum: Dell  Ubuntu Support
---

### Post by YuriBCN on 2007-06-24
Running 64bit Feisty on Inspiron 1501: have tried to install the windoze wireless card driver via ndiswrapper following instructions found at a couple of sites, but to no avail.

Log:
- Formatted HD to remove pointless partitions and crapware; reinstalled Vista 32bit (which came with 1501), incl. ATI video driver downloaded from ATI site.
- Installed Ubuntu 7.04 64bit (incl. GRUB dual boot), which detected everything and works great, as long as I connect via cable, once the connection has been configured. I can even configure the wireless connection, as the corresponding fields are there in the Network Manager dialogue. 
- Tried suggested installation of windoze wireless drivers (first tried with R151517, then with R140747) using ndiswrapper. I even went through the whole process of reinstalling everything so as to start with a clean slate. What I end up with, every time, is that **the wireless option disappears altogether from the Network Manager config dialogue**, even though the Ubuntu tells me the driver has been installed successfully and it 'sees' the hardware! Oh, and the little WiFi status light just above the keyboard **does NOT go out** at any time.

Wireless works fine under Vista. This is most embarrassing since I am trying to convince my mates how cool Linux is!

Anyone have any ideas? Am I using the wrong drivers (i.e. it's neither R151517 nor R140747)?

>> (3 hours later)... Further info... I just found out the Vista driver is 'bcmwl6.sys'. Should I try with this? Any idea where Vista keeps it hidden away?

Also interested in driver/s for corresponding ATI card, as screen flickers on hibernation.
THX.

BTW... very happy with minimalist 1501, which is exactly what I need for work (no pointless multimedia, oversized capacities/capabilities for video and gaming, etc.) and such I really don't need.

---

### Post by Unicast on 2007-06-24
Would this work for the broadcom card in your 1501?

[http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated](http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated)

---

### Post by Damavik on 2007-06-24
I have the same problems!
My wi-fi is working correct, but it can't connect to other computer!
The problem with ATI is the same!

---

### Post by Damavik on 2007-06-24
Oh! This is not all!
On my Dell inspiron 1501 i have a great problem with conexant modem!

---

