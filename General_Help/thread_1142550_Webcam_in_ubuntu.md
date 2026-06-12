---
title: "Webcam in ubuntu"
date: 2009-04-29
forum: General Help
---

### Post by Thimking on 2009-04-29
i am not able to access my laptop webcam in ubuntu 8.10,,,,
can u please help me???

---

### Post by Tibuda on 2009-04-29
Have you installed [cheese]("apt:cheese")?

Also, open a terminal and type lsusb
This is what I get in my Laptop, you can see my webcam there:
```
$ lsusb
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 002: ID 0402:5602 **ALi Corp. Video Camera Controller**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 04f3:0216 Elan Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by WildeBeest on 2009-04-29
This worked for me, albeit I have the VX-1000.
 
But, it should work for others..
 
[http://ubuntuforums.org/showthread.php?t=1034988](http://ubuntuforums.org/showthread.php?t=1034988)

---

