---
title: "Computer sets wireless driver as unclaimed when rebooting"
date: 2011-11-12
forum: Desktop Environments
---

### Post by curan on 2011-11-12
Hi all,

I've just installed Xubuntu 11.10 on an old HP Pavilion DV6000 machine, with the Broadcom BCM4311 NIC.

At first it didn't work with the clean install(the firmware missing message), so i added the driver from the 'additional drivers' option. This still didn't work(when using 'lshw -c network, it showed the device was unclaimed), so i then installed the Ndiswrapper tool, found the windows driver and installed it. This worked but only until i reboot the machine. After this, the device is again sat as unclaimed. If i then remove the driver from the Ndiswrapper and install it again, the wireless works fine again.

The above procedure was also necessary when i was running Ubuntu 11.04, but it didn't have the problem i am experiencing now.

Any gurus with some great suggestions regarding this annoying issue?

---

### Post by bkratz on 2011-11-12
> **curan said:**
> Hi all,

I've just installed Xubuntu 11.10 on an old HP Pavilion DV6000 machine, with the Broadcom BCM4311 NIC.

At first it didn't work with the clean install(the firmware missing message), so i added the driver from the 'additional drivers' option. This still didn't work(when using 'lshw -c network, it showed the device was unclaimed), so i then installed the Ndiswrapper tool, found the windows driver and installed it. This worked but only until i reboot the machine. After this, the device is again sat as unclaimed. If i then remove the driver from the Ndiswrapper and install it again, the wireless works fine again.

The above procedure was also necessary when i was running Ubuntu 11.04, but it didn't have the problem i am experiencing now.

Any gurus with some great suggestions regarding this annoying issue?

This will take care of you even in 11.10

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

note:
you probably will need to remove ndiswrapper

---

### Post by curan on 2011-11-12
Thanks, that did the trick!

---

### Post by bkratz on 2011-11-12
> **curan said:**
> Thanks, that did the trick!

Glad to hear that it worked for you, enjoy!

---

