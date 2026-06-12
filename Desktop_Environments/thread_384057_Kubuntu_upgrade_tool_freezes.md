---
title: "Kubuntu upgrade tool freezes"
date: 2007-03-14
forum: Desktop Environments
---

### Post by dollydoll on 2007-03-14
HI,
The past week I've been trying to get the upgrade for Kubuntu going on my Acer Aspire 5570, that runs Ubuntu Edgy 6.10, but it simply freezes, and I end up killing the application.
The first attempt when running the upgrade tool ended up with a  crash and a bug report tool, that didn't work either. Unluckily I didn't happen to take a screenshot of my Desktop.
Does anyone know whether this is a known issue, or hardware related?

thanks a bunch

here are my specs:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:09.0 CardBus bridge: Texas Instruments Unknown device 8039
0a:09.2 Mass storage controller: Texas Instruments Unknown device 803b

---

### Post by jimbren on 2007-03-14
What exactly are you doing to "get the upgrade?" Installing Kubuntu isn't really an upgrade--you're really just installing a metapackage.

This has always worked flawlessly for me in the past:
```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```

This will ensure your system is completely up to date.

Then
```
sudo apt-get install kubuntu-desktop
```

The packages will download and install, and you'll be asked to pick your default login manager, GDM or KDM.  

And that's all there should be to it.  

jimbo

---

### Post by dollydoll on 2007-03-14
Hi

thanks for your reply.
This time around, the updates were done with Adept Updater. 
I already installed kubuntu-desktop right after I installed Ubuntu on the laptop; therefore, I already run Kubuntu.
The Adept updater finished the updates and advised that there was an upgrade for my current kubuntu package. 
I accepted to go for it, and the Kubuntu upgrade tool crashed when installing the newly downloaded version of kubuntu..i hope this makes things clearer.
Thanks a bunch

---

