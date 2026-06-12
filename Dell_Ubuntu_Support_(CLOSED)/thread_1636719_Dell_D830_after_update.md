---
title: "Dell D830 after update"
date: 2010-12-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sledjockey on 2010-12-03
I did a software update yesterday and today my video is messed up. What it does is kind of bizarre:

On my second monitor, it is as if the picture is shifted to the left and my mouse is actually clicking in "no man's land" although the system interprets the image as being that inch further right than what it appears.

Screenshots don't look right, but I can take a picture with my phone to show if this does not make sense.



At any rate, now what? I am lost and not even sure what to Google for an answer. Everything I have tried to use as a search thus far doesn't result in anything that is related.

Edit:
I am using 10.04 LTS btw.....

---

### Post by sikander3786 on 2010-12-03
I don't know which graphics card is there in D830. Are there any proprietary drivers installed for that?

First of all try reconfiguring your graphics by,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot and see if that makes any different. Otherwise post the details regarding graphics card.

---

### Post by sledjockey on 2010-12-03
It did not fix it.....  Here is my info:



00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)


Edit:

FYI: I posted more information than requested in case there was something else installed that might be causing the problem with my video. Just a precaution.

---

### Post by sikander3786 on 2010-12-03
See if there is an xorg.conf and if there is one, post its output.

```
cat /etc/X11/xorg.conf
```

---

### Post by sledjockey on 2010-12-03
cat: /etc/X11/xorg.conf: No such file or directory

---

### Post by sledjockey on 2010-12-06
Bump

---

### Post by sledjockey on 2010-12-06
Ended up having to do a complete reinstall to get this fixed. Whatever packages were updated on the day this started really jacked up my video. It was bad enough that the system was essentially unusable at my desk.

My upgrade to 10.10 also errored out with that "Could not calculate upgrade" message that seems to have everyone stumped. In the end, I had to play like it was the "Redmond Virus" and just "restore" my system......

Good thing the programs are easy to reinstall and with a backup of my home directory there should be few settings I have to mess with..... I hope.

Thank you for your assistance.

---

