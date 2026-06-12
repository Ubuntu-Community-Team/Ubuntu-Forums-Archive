---
title: "Ubuntu &amp; USB3 (not working)"
date: 2014-02-23
forum: Desktop Environments
---

### Post by mtweldon on 2014-02-23
Just recently installed the newest version of ubuntu desktop. 

Having issues getting it to see my USB3 ports. if I plug anything into it, it sees nothing. 


lsusb gives me this.

> Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04e8:6054 Samsung Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bc2:3312 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 004 Device 002: ID 1b1c:0a60 Corsair Vengeance K60 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I have 8 USB 2.0 ports and 4 USB3, two on the back + 2 on the front attached via 1 cable to motherboard.

Not even sure how to tell which one could potentially USB3...

dmesage after plugging / unplugging from USB3 results in nothing.

not sure where to go from here.

---

### Post by Yellow Pasque on 2014-02-23
What kind of mobo is it?

---

### Post by mtweldon on 2014-02-23
Gigabyte ga-990fxa-ud3 am3+ amd 990fx

---

### Post by Yellow Pasque on 2014-02-23
LOL. I knew it. See post 16 here: [http://ubuntuforums.org/showthread.php?t=2143433](http://ubuntuforums.org/showthread.php?t=2143433)

---

### Post by QIII on 2014-02-23
By way of explanation, you took IOMMU control away from the motherboard and gave it over to software control.

---

### Post by mtweldon on 2014-02-24
Awesome, thanks so much!


Post #16 Worked!

---

### Post by Yellow Pasque on 2014-02-24
You're welcome. Mark thread solved.

---

