---
title: "Dell Inspiron E1505: No Wireless Internet"
date: 2011-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RedStarYellowSun on 2011-05-02
I just installed Ubuntu 11.04 in this laptop. I can connect to our wireless Internet in the other operating system (Windows XP), but the only way I can go online in Ubuntu is by plugging it into the cable modem.

Could someone help me, please? _&#915;L*

Here is a some information that I was able to compile:
>To "nm-applet":```
kalayaan001@Kalayaan-MM061:~$ nm-applet
An instance of nm-applet is already running.

** (nm-applet:1727): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.
```How can we initialize the D-Bus manager?

> To "nm-tool":```
kalayaan001@Kalayaan-MM061:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:19:B9:85:01:CA

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off
```

> To "rfkill list":```

kalayaan001@Kalayaan-MM061:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

> To "lspci":```
kalayaan001@Kalayaan-MM061:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

I hope that the information (and their division) helped.

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by rajush on 2011-05-02
yea...even i've been trying to solve the issue, but no luck. I've tried every possible solutions :( Hopefully somebody will solve the issue :???:

---

### Post by mörgæs on 2011-05-02
There have been posted several bug reports concerning wirefree in Launchpad recently. I would stay with 10.10 for at least a month more.

---

### Post by Hippytaff on 2011-05-02
It might have something to do with the broadcom drivers. This might help

---

### Post by RedStarYellowSun on 2011-05-02
> **rajush said:**
> yea...even i've been trying to solve the issue, but no luck. I've tried every possible solutions :( Hopefully somebody will solve the issue :???:
Thanks for trying, though.

It seems that I am far from the only one experiencing this problem. Hopefully, a solution does come-up soon.

> **mörgæs said:**
> There have been posted several bug reports concerning wirefree in Launchpad recently. I would stay with 10.10 for at least a month more.
That sounds wise. If a solution is not found soon, I'll downgrade to 10.10.

> **Hippytaff said:**
> It might have something to do with the broadcom drivers. This might help
That seems plausible.

Everyone, thanks for the reply! It is much appreciated.

Take care,
RedStarYellowSun

---

### Post by Nightstalker363 on 2011-05-05
> **RedStarYellowSun said:**
> Thanks for trying, though.

It seems that I am far from the only one experiencing this problem. Hopefully, a solution does come-up soon.


your not the only one with that problem on this type of machine.  I can access the wireless network but if i do a softlock using the Fn-f2 keys i'm unable to unlock it without restarting the computer.  It almost seems like the driver's softunlock feature is broken since i'm able to lock it.

---

### Post by RedStarYellowSun on 2011-05-05
> **Nightstalker363 said:**
> your not the only one with that problem on this type of machine.  I can access the wireless network but if i do a softlock using the Fn-f2 keys i'm unable to unlock it without restarting the computer.  It almost seems like the driver's softunlock feature is broken since i'm able to lock it.
I posted my problem Ask Ubuntu and got *some* progress, though not the solution... at lest, not yet.
[http://askubuntu.com/questions/39508/how-do-you-solve-the-problem-of-a-laptops-inability-to-detect-wireless-networks](http://askubuntu.com/questions/39508/how-do-you-solve-the-problem-of-a-laptops-inability-to-detect-wireless-networks)

Have you tried Ask Ubuntu yet? They might be able to help you out, too.

Take care,
RedStarYellowSun

---

### Post by crush304 on 2011-05-08
disable/remove the broadcom sta driver

install firmware-b43-installer

---

### Post by Biaspoint on 2011-05-08
From askubuntu.com:)

[LIST]
[*]open the '*Synaptic Package Manager*' and search for 'bcm'
[*]uninstall the '*bcm-kernel-source*' package
[*]make sure that the '*firmware-b43-installer*' and the '*b43-fwcutter*' packages are installed
[*]reboot
[/LIST]
Worked for me, system: Dell Inspiron E1505.  The site also listed the step of modifying the blacklist conf file which I did and then had to undo to get it to work.

---

### Post by nm_geo on 2011-05-09
> **RedStarYellowSun said:**
> I posted my problem Ask Ubuntu and got *some* progress, though not the solution... at lest, not yet.
[http://askubuntu.com/questions/39508/how-do-you-solve-the-problem-of-a-laptops-inability-to-detect-wireless-networks](http://askubuntu.com/questions/39508/how-do-you-solve-the-problem-of-a-laptops-inability-to-detect-wireless-networks)

Have you tried Ask Ubuntu yet? They might be able to help you out, too.

Take care,
RedStarYellowSun


Since you have the B44 wired driver you need the ssb module.  I would recommend you install b43-fwcutter and the  firmware-b43-installer. The two previous poster gave you good information.
The STA driver and the ssb module do not play nice together.
In addition you might have some blacklist issues that you may need to fix.

Copy and paste this in terminal and then paste back here.

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
```

---

### Post by abovecrazykid on 2011-05-10
This did it thanx

---

### Post by abovecrazykid on 2011-05-10
> **Biaspoint said:**
> From askubuntu.com:)

[LIST]
[*]open the '*Synaptic Package Manager*' and search for 'bcm'
[*]uninstall the '*bcm-kernel-source*' package
[*]make sure that the '*firmware-b43-installer*' and the '*b43-fwcutter*' packages are installed
[*]reboot
[/LIST]
Worked for me, system: Dell Inspiron E1505.  The site also listed the step of modifying the blacklist conf file which I did and then had to undo to get it to work.




Thanx this worked well

---

### Post by kyleoxt1982 on 2011-09-05
I had already tried some other methods, so the first time I tried this, it did not work.  But I did a re-install of Ubuntu from scratch, and then this method worked great.  TRY THIS METHOD BEFORE ANYTHING ELSE!  Thanks.

---

