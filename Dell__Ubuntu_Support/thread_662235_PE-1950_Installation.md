---
title: "PE-1950 Installation"
date: 2008-01-08
forum: Dell  Ubuntu Support
---

### Post by skmassey on 2008-01-08
I'm having trouble getting my raid controller working under 7.10 server.  I couldn't get the raid controller recognized during the install, so I removed it and installed ubuntu to a usb HDD.  The raid controller should use the megaraid_sas driver.  I have blacklisted the mptsas module and added the megaraid_sas module to "/etc/modules".  The server boots with the controller installed, but after boot the drives are not detected.  I have two 300GB 15k RPM HDD's installed in a RAID-1.  Any help would be greatly appreciated.

Thank you

---

