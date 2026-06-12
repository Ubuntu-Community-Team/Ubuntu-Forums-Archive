---
title: "Dell Vostro 3300 Nvidia GT310 anyone?"
date: 2010-04-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by avilella on 2010-04-30
Hi,

Has anyone tried Linux on a Dell Vostro 3300 with Nvidia GT310 card?

---

### Post by godsiem on 2010-05-05
Hi avilella,

I am writing this reply from my Dell Vostro 3300 with Nvidia GT310... It works pretty well, little extra configurations were required after installing Ubuntu 10.04. The only thing I had to do was to enable the drivers for Nvidia and Wireless card, reboot the machine, and I everything was working perfectly. You can refer to this post for more details: [http://vikashazrati.wordpress.com/2010/04/26/dell-vostro-3700-ubuntu-9-10-and-window-7/](http://vikashazrati.wordpress.com/2010/04/26/dell-vostro-3700-ubuntu-9-10-and-window-7/). It was originally for the model 3700, but it also works with the 3300 with Nvidia cards.

So, no problems at all with Ubuntu 10.04 in the Vostro 3300!... it is actually very good :)

Cheers!

---

### Post by lilly-marlene on 2010-05-05
Well, for me it is not so fine :( Tried to install kubuntu 10.04 on my Vostro 3300 with GeForce 310 - from LiveCD everything worked perfectly. At the first boot after install i received the error message - problem with drm nouveau. After the attempt to login in KDE i received the blackscreen and system hangs completely. Tried to blacklist nouveau but after that couldn`t login even in the console. So now i`m back to kubuntu 9.10 and searching for solution.

---

### Post by wconstantine on 2010-06-03
What wireless manufacturer has the Vostro 3300 got? I'm looking if it's compatible with the aircrack-ng suite.

---

### Post by godsiem on 2010-06-03
Hello,

According to "lspci":
"
12:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
"

In the "Hardware Drivers" option, in ubuntu Administration menu, I get that it is using the proprietary driver from Broadcom:
"
These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware.
"

Cheers!

---

### Post by wconstantine on 2010-06-03
That is awesome news. Thank you very much.

---

