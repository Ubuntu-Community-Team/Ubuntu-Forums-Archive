---
title: "ubuntu-desktop 9.04 is slow to work on P4"
date: 2009-05-27
forum: General Help
---

### Post by W03L on 2009-05-27
Hi.
Install ubuntu-desktop 9.04 on P4(1.7 intel, motherboard intel, 256MB, 80Gb, built - in video card) and it work very slow (each operation long time to think). From the same disk I'm install on P3 (1000 Celeron, motherboard elitegroup, 256MB, 20Gb, built - in video card) and it work fine. What is this?

---

### Post by Steelmourne on 2009-05-28
It might be the BIOS on the P4 motherboard.

---

### Post by dmizer on 2009-05-28
Most likely a video driver problem. Please post the output of:
```
lspci
```

---

### Post by W03L on 2009-05-28
administrator@triton:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82) 
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02) 
01:06.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 02)

---

### Post by dmizer on 2009-05-28
Take a look here: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by cwmoser on 2009-05-28
might be that you have IPV6 enabled.

I disabled ipv6 and my PC runs much faster.

[HTML]

**IPv6 Quick (Firefox) Fix**

If you can't access the web through Firefox, though you know you have an internet connection via your modem/router try the following:

Enter about:config in Firefox's address field.

Enter ipv6 in the new Filter: field.

Double click on the line left in the display window to change it's boolean value to true.

Restart Firefox.

& that should be that...  

____________________

[B]
Disable IPv6 Globally[/B]

Unlike the method of editing /etc/modprobe.d/aliases, the following method does not run the risk of being overwritten. 

Do the following to disable IPv6 globally:

1. To verify that the IPv6 module is loaded type the following from a terminal:

handy@birdfish:~$ lsmod | grep ipv6
ipv6 265856 10

2. Then from a terminal type:

handy@birdfish:~$ sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6

3. Restart

4. To verify that the IPv6 module is not loaded type the following from a terminal:

handy@birdfish:~$ lsmod | grep ipv6
handy@birdfish:~$

If for whatever reason the above method does not work, type sudo nano -w /etc/modprobe.d/blacklist & enter the line blacklist-ipv6, then do steps 3. & 4. as above.

____________________

The reason for the first (DNS) problem which strikes lots of modem/routers is due to their windows centric design.

The reason for the second (IPv6) problem is due to the cheap quality of the router, which is also responsible for the first problem...
[/HTML]

---

### Post by dmizer on 2009-05-28
The above mentioned method will not disable IPv6 in Jaunty. I don't think this is an IPv6 problem anyway.

---

### Post by W03L on 2009-05-28
> **dmizer said:**
> Take a look here: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

thanks, it much faster now

---

