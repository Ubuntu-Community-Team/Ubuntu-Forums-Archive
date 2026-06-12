---
title: "wlan0: no such device"
date: 2006-01-19
forum: Desktop Environments
---

### Post by Pojodojo on 2006-01-19
I am having trouble with the wireless settings on ubuntu. I have gone through [this]("http://ubuntuforums.org/showthread.php?t=25683") walkthrough and the similar one on the forums here multiple times to no avail.

I also have the GUI ndiswrapper installed on here to allow the changing of drivers more easily. However I did it manually many times before switching for ease of use. 

I have the Broadcom bcmwl5.inf driver, which i am posative is the correct driver. I am on a Dell Inspiron 1300 w/ mpci dual band internal wireless card.

It seems to all work correctly until i run ```
ndiswrapper -l
``` and it returns ```
Installed ndis drivers:
bcmwl5  invalid driver!

```

If it helps i will include my lspci which has an unidentified Broadcom device. 
```
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:03.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
dan@Walter:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:03.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)

```

It just does not see the wireless adapter and will not make a wlan0. thats my take at least. Thanks for any help.

---

### Post by Pojodojo on 2006-01-19
problem solved.  I only had the inf file, and not the sys file, but i solved that by using a link to teh sipped broadcom driver, which contained both, and then followed the walkthrough again and now i am on the wireless.   

hot damn i feel good!

---

