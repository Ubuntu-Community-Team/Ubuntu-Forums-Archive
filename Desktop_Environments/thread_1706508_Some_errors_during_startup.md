---
title: "Some errors during startup"
date: 2011-03-13
forum: Desktop Environments
---

### Post by Dr.Paneas on 2011-03-13
After updating my kernel to 2.6.38 rc, an error message appears every time I restart the computer, during startup. The screen goes so fast that I can't read information about that error, and then Ubuntu desktop appears on the screen.

Where are the logs about that ?

---

### Post by Krytarik on 2011-03-14
"/var/log/messages"

You can use "System -> Administration -> Log File Viewer" to check logs.

Greetings.

---

### Post by Dr.Paneas on 2011-03-14
Hey thanks man. I went over that, clicked on boot section on the left but...
... "(Nothing has been logged yet.)"

---

### Post by Krytarik on 2011-03-14
> **Dr.Paneas said:**
> Hey thanks man. I went over that, clicked on boot section on the left but...
... "(Nothing has been logged yet.)"
The same at my system, ironically. :P
Check "messages", like I said.

---

### Post by Dr.Paneas on 2011-03-15
I found something, although I can't fix it. I think it's some atheros error or somethin

```

Mar 16 03:25:15 ubuntu kernel: [    4.659037] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Mar 16 03:25:15 ubuntu kernel: [    5.371385] r8169 0000:05:00.0: eth0: link up
Mar 16 03:25:15 ubuntu kernel: [    5.371584] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Mar 16 03:25:19 ubuntu kernel: [    8.475645] **ath3k: probe of 1-1.5:1.0 failed with error -5**
Mar 16 03:25:19 ubuntu kernel: [    8.475687] usbcore: registered new interface driver ath3k
Mar 16 03:25:19 ubuntu kernel: [    8.606385] audit_printk_skb: 21 callbacks suppressed
Mar 16 03:25:19 ubuntu kernel: [    8.606387] type=1400 audit(1300238719.199:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1312 comm="apparmor_parser"
Mar 16 03:25:19 ubuntu kernel: [    8.606436] type=1400 audit(1300238719.199:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1312 comm="apparmor_parser"
Mar 16 03:25:19 ubuntu kernel: [    8.610153] ppdev: user-space parallel port driver
```

---

### Post by Krytarik on 2011-03-15
It's the driver for your wireless card/chip. Since you seem to have internet access, that apparently doesn't matter. ;-)

---

