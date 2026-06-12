---
title: "[SOLVED] Dell XPS1530 - Ubuntu 8.04 not recognizing my internal bluetooth device"
date: 2008-05-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by x001 on 2008-05-07
Hello all,

Ubuntu 8.04 (32-bit) has been working flawlessly on my XPS1530 laptop (including the biometric device). Today I wanted to try pairing my bluetooth (Moto S9) headset with my laptop but quickly realized the ubuntu is unble to detect the internal bluetooth module. I have searched the Internet and cant find any solutions or even where to start.

When I try lusb I get the following out and "Bluetooth" is not listed:

```
x2ws@xps1530:~$ lsusb
Bus 007 Device 002: ID 1058:0702 Western Digital Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 005 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 005 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 0000:0000  

```

Also sudo lsusb -v|grep -i bluetooth comes back with nothing.
hciconfig up comes back with: Can't get device info: No such device

Any help/tips is greatly appreciated.

---

### Post by x001 on 2008-05-09
Sorry for the bump... anyone have any ideas I can try?

---

### Post by prshah on 2008-05-09
> **x001 said:**
> ubuntu is unble to detect the internal bluetooth module. I have searched the Internet and cant find any solutions or even where to start.


Do you have a hardware button to enable/disable bluetooth?

---

### Post by x001 on 2008-05-09
> **prshah said:**
> Do you have a hardware button to enable/disable bluetooth?

Thank you for taking the time to help me out.

There is a hardware switch for enabling Bluetooth and it is enabled. It is the same button to enable/disable WiFi and wifi works. I also looked at Dell's Linux site [http://linux.dell.com/wiki/index.php/Ubuntu_8.04]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04") and did not find any useful info on Bluetooth for the XPS 1330. 1330 is almost identical to the 1530.

---

### Post by Coder_ak on 2008-07-04
The solution is quite easy. Vista disable internal bluetooth module and you have to run it to enable again.
But, there is utility on Dell site [http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R159805&formatcnt=1&libid=0&fileid=213714](http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R159805&formatcnt=1&libid=0&fileid=213714)
Run in from Vista (you can use LiveCd) and Bluetooth come back )

---

### Post by Coder_ak on 2008-07-04
The solution is quite easy. Vista disable internal bluetooth module and you have to run it to enable again.
But, there is utility on Dell site [http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R159805&formatcnt=1&libid=0&fileid=213714](http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R159805&formatcnt=1&libid=0&fileid=213714)
Run in from Vista (you can use LiveCd) and Bluetooth come back )

---

### Post by x001 on 2008-07-04
I ended up calling Dell Tech Support and they had me install Vista and then determined that it was a hardware problem. They sent me a new bluetooth module, I replaced it and bluetooth now works in Ubuntu.

---

### Post by prshah on 2008-07-04
> **x001 said:**
> I ended up calling Dell Tech Support and they had me install Vista and then determined that it was a hardware problem. They sent me a new bluetooth module, I replaced it and bluetooth now works in Ubuntu.

OK! Please mark the thread solved; click on "Thread Tools" _near_ the top right hand side of the page, then select "Mark Thread as Solved".

---

