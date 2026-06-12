---
title: "Inspiron 1420 Wireless doesn't work after upgrading to hardy"
date: 2008-07-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by niska on 2008-07-29
I've upgraded to hardy using a wired connection including all updates. 
After the upgrade both the wireless connection and the led stopped working.
 Installing the package linux-backports-modules-2.6.24-19-generic got the led working,
 but still wireless networks are not recognized. Also,
 there are no drivers appearing on the hardware drivers application at all.

Before the upgrade gutsy was installed with the dell dvd.

---

### Post by knighthawk1234 on 2008-07-29
I too am having the same problem with my dell 6000 laptop. I installed hardy and i had no wi-fi. After performing some of the steps in other posts i got my wifi light to work but still no networks showed up. Some have posted that the latest system updates have fixed the wireless driver problems but mine continue. My system is up-to-date but still no wi-fi. 

 Other then that everything else works great. Very nice, clean OS. 

 I'm a total noob when it comes to linux and ubuntu but I'm welling to learn it. If anyone could walk me though the process of tring to fix it I would be very greatfull.

---

### Post by linux_tech on 2008-07-30
What brand wireless adapter is it?  Did you try uninstalling Network Manager and reinstall it. Did you check device manager info?

---

### Post by mondoUNC on 2008-07-30
I encountered the same wireless problem when converting my sister's Inspiron from Vista to Ubuntu.

[This guide]("http://ubuntuforums.org/showthread.php?t=769990") fixed the problem for me

Hope that helps.

---

### Post by niska on 2008-07-30
Here's my lspci:
```
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
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

Reinstalling network manager did not solve the problem, actually it made the network setting gui very slow and it now indicates that all network connections are not configured (wired and wireless), although wired still works fine.

Installing dsiwrapper doesn't seem right to me, I bought this laptop with ubuntu preinstalled so I believe I should have all the drivers I need.

---

### Post by lynchman on 2008-07-30
Hmmm... I just updated (I was already running Hardy) last night over a wired connection, and this morning (fresh boot) my wireless was dead.  I haven't looked into it too much yet and I don't have my 1420n in front of me now, but I'm not sure if this is a upgrade problem (gusty -> hardy) or just with the latest packages - I'm suspecting the latest pacakges.  I know that a new kernel was part of the update that I did.  It has been about 2 weeks since I last ran an update.

I'm using (and have been) wicd instead of network manager.  Wicd fixed my initial problems with hardy and wireless, but I'm not too sure what's up now.  I'll try to play with it tonight to see what's up.

---

### Post by unoodles on 2008-07-30
Its because Hardy uses the iwl3945 but Gutsy used the ipw3945.
I have the inspiron 1420n. My wireless works fine, but I did a clean reinstall instead of an upgrade to Hardy. You could try installing the linux-backports-modules.

---

### Post by niska on 2008-08-03
> **unoodles said:**
> Its because Hardy uses the iwl3945 but Gutsy used the ipw3945.
I have the inspiron 1420n. My wireless works fine, but I did a clean reinstall instead of an upgrade to Hardy. You could try installing the linux-backports-modules.

OK, a clean install solved the problem. I am still displeased with the fact that dell did not release a reinstallation dvd for Hardy.

---

### Post by TimDaniels on 2008-08-09
> **niska said:**
> OK, a clean install solved the problem.

Does a clean install leave settings intact, or must one start from Square One again?

*TimDaniels*

---

### Post by niska on 2008-08-10
> **TimDaniels said:**
> Does a clean install leave settings intact, or must one start from Square One again?

*TimDaniels*

I had my /home folder separated in it's own partition when I first installed Gutsy, so when installing Hardy I only formatted the root partition.

The packages installed were removed but once reinstalled they resumed their previous settings.

---

### Post by TimDaniels on 2008-08-10
> **niska said:**
> I had my /home folder separated in it's own partition when I first installed Gutsy, so when installing Hardy I only formatted the root partition.

The packages installed were removed but once reinstalled they resumed their previous settings.

Does the installer see that "/home" is mounted on another partition and leave it out of the "/" hierarchy?

I guess I'll have to start using a separate partition for /home, too.  For now, I'll try just copying the /home directory to an external hard drive and then copying it back to the new installation.

*TimDaniels*

---

### Post by niska on 2008-08-10
> **TimDaniels said:**
> Does the installer see that "/home" is mounted on another partition and leave it out of the "/" hierarchy?

*TimDaniels*

Of course the installer sees if it's a different partition.

You would have to redefine the partition's mount point as /home but that's very simple.

---

