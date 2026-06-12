---
title: "How to &quot;reset&quot; a scanner"
date: 2006-09-02
forum: Desktop Environments
---

### Post by dihfg on 2006-09-02
I have a problem with my scanner which I cannot solve. Here is the situation:

PC dual-boot (Dapper Drake, WindowsXP)
EPSON Perfection 1670 Scanner, Linux driver installed. 

When I boot Ubuntu the scanner is recognised by the system (vendor=0x04b8 [EPSON], product=0x011f [EPSON Scanner] at libusb:005:003) but the scanner's ready lamp is not on and it does not accept any commands. Calling iscan results in an error message "...check scanner status").
 
When I boot Windows however the lamp is on and the scanner works. AND NOW THIS: when I leave Windows and reboot to Ubuntu (scanner still connected) it works and scanning is possible eg by using XSane.

It seems as if Windows executes some internal reset on the scanner and Ubuntu does not (my guess, but I am no expert). 

Is there someone on this forum who knows this problem and can suggest a workaround?

---

