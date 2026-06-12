---
title: "Inspiron 1501 - no wifi"
date: 2010-08-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LostViking99 on 2010-08-15
I just installed ubuntu 10.04 on my dell inspiron 1501, everything appears to work except for the networking. I use wireless, and the device is shown as 'Disabled' under the lshw command in terminal.

The laptop doesnt have access to a physical connection, but I could download files from another pc and transfer them.

How do I turn on my wireless radio? I tried the keyboard shortcut, didn't work. There doesn't appear to be an option to turn the radio on/off in ubuntu. I'm guessing this issue has already been solved so if someone could point me in the right direction that would be great.


If it helps, I have a Broadcom Corp BCM4311 802.11b/g WLAN card.

---

### Post by LostViking99 on 2010-08-15
I just installed ubuntu 10.04 on my dell inspiron 1501, everything appears to work except for the networking. I use wireless, and the device is shown as 'Disabled' under the lshw command in terminal.

The laptop doesnt have access to a physical connection, but I could download files from another pc and transfer them.

How do I turn on my wireless radio? I tried the keyboard shortcut, didn't work. There doesn't appear to be an option to turn the radio on/off in ubuntu. I'm guessing this issue has already been solved so if someone could point me in the right direction that would be great.

If it helps, I have a Broadcom Corp BCM4311 802.11b/g WLAN card.

---

### Post by cariboo on 2010-08-15
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by sureshsaragadam on 2010-08-16
So You want to Enable/Disable your Wifi

There is a Network Manager Applet in the upside right corner of your panel,  right click it to find Enable/Disable your Wireless or Network.

---

### Post by spjackson on 2010-08-16
I too have an Inspiron 1501 with a BCM4311 802.11b/g WLAN card and it works very well under Ubuntu 10.04 Desktop amd64 that I recently installed.
Do you have the proprietary driver enabled? System->Administration->Hardware Drivers. I am using the Broadcom STA proprietary driver.
I didn't take any special steps to get it working other than enabling this proprietary driver - it worked from the Live CD once I enabled the driver.

---

### Post by Sanity8080 on 2010-10-23
> **spjackson said:**
> I too have an Inspiron 1501 with a BCM4311 802.11b/g WLAN card and it works very well under Ubuntu 10.04 Desktop amd64 that I recently installed.
Do you have the proprietary driver enabled? System->Administration->Hardware Drivers. I am using the Broadcom STA proprietary driver.
I didn't take any special steps to get it working other than enabling this proprietary driver - it worked from the Live CD once I enabled the driver.


When I try that, it says no proprietary drivers found

---

