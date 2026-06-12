---
title: "Lost wireless driver, cannot reinstall"
date: 2010-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rackstar on 2010-12-27
Hi,

I'm suffering from this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658307](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658307) involving suspend/resume. As everyone experiencing this bug had a Broadcom 43x driver. I thought to change my driver in as there were two in "Extra drivers" (can be wrong translated, dutch installation here).

But then the horror began. It uninstalled the STA driver currently installed (possibly causing my suspend/resume issues), but did not correctly install the other one "Broadcom B43 wireless driver" "Supported chipsets:- BCM4306/3- BCM4311- **BCM4312**- BCM4318".

And as for now, I can't remove that driver, nor install the other one. (None is indicated as active btw)

More information about my setup (Dell studio 1558 ):
> ruben@ruben-dell:~$ sudo lshw -class network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: b8:ac:6f:67:ff:5b
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.0.105 latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:47 ioport:5000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff memory:f0420000-f043ffff


> 04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)


I tried this but it failed: > sudo apt-get --reinstall install bcmwl-kernel-source
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
De volgende pakketten werden automatisch geïnstalleerd en zijn niet langer nodig:
  wine1.3-gecko libwebkit1.1-cil
U kunt deze verwijderen via 'apt-get autoremove'.
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 1 opnieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
1 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 0B/897kB aan archieven opgehaald worden.
Door deze operatie zal er 0B extra schijfruimte gebruikt worden.
(Database inlezen ... 294442 bestanden en mappen geïnstalleerd.)
Voorbereiden om bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu5 te vervangen (door .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb) ...
Removing all DKMS Modules
Done.
Uitpakken van vervangende bcmwl-kernel-source ...
Instellen van firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: fout bij afhandelen van firmware-b43-installer (--configure):
 subproces installed post-installation script gaf een foutwaarde 1 terug
Instellen van bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu5) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
Building only for 2.6.35-24-generic
Building for architecture x86_64
Building initial module for 2.6.35-24-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-24-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
Fouten gevonden tijdens behandelen van:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


Does someone have an idea? 

[rant]
I was trying to fix my bluetooth and suspend/resume yesterday, and today I'm here with a more broken system than before... I thought Dell would be a "safe" choice for Ubuntu, however, I probably should have done more thorough research.
[/rant]

---

### Post by amsterdamharu on 2010-12-27
I think you can try this driver, it worked for several users:

firmware-b43-installer

You need an Internet connection to install it because the b43-fwcutter will get the driver from a website. If you have cable Internet you can install it using the following command:

```
sudo apt-get install firmware-b43-installer
```

If you don't have Internet you need to download 1 deb files and an archive.
Install this deb file first:
[http://packages.ubuntu.com/en/maverick/b43-fwcutter](http://packages.ubuntu.com/en/maverick/b43-fwcutter)
Then download this file:
[http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
Put that file on your desktop and execute the following commands:
```
cd ~/Desktop
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo b43-fwcutter -w "/lib/firmware" wl_apsta_mimo.o
```

Actually the firmware-b43-installer has a script that deletes the /lib/firmware/b43 directory so you might want to do this manually
```
sudo rm -rf /lib/firmware/b43
```

---

### Post by Rackstar on 2010-12-27
Thanks for the quick response!

However, I tried the command (I also have wired access to the internet):
> sudo apt-get install firmware-b43-installer
[sudo] password for ruben: 
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
firmware-b43-installer is reeds de nieuwste versie.
De volgende pakketten werden automatisch geïnstalleerd en zijn niet langer nodig:
  wine1.3-gecko libwebkit1.1-cil
U kunt deze verwijderen via 'apt-get autoremove'.
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
1 pakketten niet volledig geïnstalleerd of verwijderd.
Door deze operatie zal er 0B extra schijfruimte gebruikt worden.
Wilt u doorgaan [J/n]? J
Instellen van firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: fout bij afhandelen van firmware-b43-installer (--configure):
 subproces installed post-installation script gaf een foutwaarde 1 terug
Fouten gevonden tijdens behandelen van:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by amsterdamharu on 2010-12-27
Well I've opened the deb file in gdebi (double clicked the deb) gone to the "included files" tab and see that that low power error comes from the following script:
```

pci=`lspci -n | grep -o "14e4:[1234567890]\+"` || true

..... bladibladibla

elif [ "`echo $pci | cut -d: -f2`" = "4315" ]; then
        echo "Not supported low-power chip with PCI id $pci!"
        echo "Aborting."
        exit 1
```In other words; your broadcom is not supported. But lshw gave you a value of BCM4312 so I'm confused.

What is the output of this command?
```
sudo lspci -n
```How about manually installing the file (see my previous post about not having cable internet).

---

### Post by amsterdamharu on 2010-12-27
Ok, do not manually install. Try this first:

```
sudo apt-get purge firmware-b43-installer
```Then install again with
```
sudo apt-get install firmware-b43-installer
```

[http://ubuntuforums.org/showthread.php?t=1630997](http://ubuntuforums.org/showthread.php?t=1630997)

---

### Post by Rackstar on 2010-12-27
I tried purging it, it did remove some KB's, but the new installation failed again with the same error.

> Uitpakken van firmware-b43-installer (uit .../firmware-b43-installer_4.150.10.5-4_all.deb) ...
Instellen van firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: fout bij afhandelen van firmware-b43-installer (--configure):
 subproces installed post-installation script gaf een foutwaarde 1 terug
Fouten gevonden tijdens behandelen van:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


Output of sudo lspci -n:
> ruben@ruben-dell:~$ sudo lspci -n
00:00.0 0600: 8086:0044 (rev 12)
00:01.0 0604: 8086:0045 (rev 12)
00:16.0 0780: 8086:3b64 (rev 06)
00:1a.0 0c03: 8086:3b3c (rev 06)
00:1b.0 0403: 8086:3b56 (rev 06)
00:1c.0 0604: 8086:3b42 (rev 06)
00:1c.1 0604: 8086:3b44 (rev 06)
00:1c.3 0604: 8086:3b48 (rev 06)
00:1c.4 0604: 8086:3b4a (rev 06)
00:1c.5 0604: 8086:3b4c (rev 06)
00:1d.0 0c03: 8086:3b34 (rev 06)
00:1e.0 0604: 8086:2448 (rev a6)
00:1f.0 0601: 8086:3b09 (rev 06)
00:1f.2 0106: 8086:3b29 (rev 06)
00:1f.3 0c05: 8086:3b30 (rev 06)
00:1f.6 1180: 8086:3b32 (rev 06)
02:00.0 0300: 1002:68e0
02:00.1 0403: 1002:aa68
04:00.0 0280: 14e4:4315 (rev 01)
07:00.0 0805: 1180:e822 (rev 01)
07:00.1 0880: 1180:e230 (rev 01)
07:00.2 0880: 1180:e852 (rev 01)
07:00.3 0c00: 1180:e832 (rev 01)
09:00.0 0200: 10ec:8168 (rev 03)
ff:00.0 0600: 8086:2c62 (rev 02)
ff:00.1 0600: 8086:2d01 (rev 02)
ff:02.0 0600: 8086:2d10 (rev 02)
ff:02.1 0600: 8086:2d11 (rev 02)
ff:02.2 0600: 8086:2d12 (rev 02)
ff:02.3 0600: 8086:2d13 (rev 02)


---

### Post by Rackstar on 2010-12-27
For some reason the STA driver was indicated as active in "Extra drivers". Though it said "Installed, but not in use". I then choose the option to remove it.

I'm going to reboot now, to clean the pipes.

---

### Post by Rackstar on 2010-12-27
Tried installing the STA driver through "Extra drivers", but it also failed on "installArchive()".

---

### Post by Rackstar on 2010-12-27
> **amsterdamharu said:**
> ]In other words; your broadcom is not supported. But lshw gave you a value of BCM4312 so I'm confused.


Could it be that it falsly detects a 4312 instead of a 4315, because I can remember that it actually was a 4315 before (however, I'm really not sure)

Is there any way to be sure what the real device is? (I have a ubuntu live USB to try out a "fresh install")

---

### Post by amsterdamharu on 2010-12-27
I have no idea what you installed but it is doing more harm than good.

Did you install linux-wlan-ng?

In that case remove that first:
```
sudo apt-get purge linux-wlan-ng
sudo apt-get purge firmware-b43-installer
sudo apt-get install firmware-b43-installer
```

---

### Post by amsterdamharu on 2010-12-27
I think it doesn't falsely detect but some other driver is getting in the way. If you boot from live usb and execute the command:
```
sudo lshw -C network
```
It should show you what's there.

---

### Post by Rackstar on 2010-12-27
Thanks for doing all this!

However, I didn't have that package installed it seems. It doesn't change a thing.

The only things I messed around with (apart from some bluetooth things yesterday) was in the "Extra drivers". A screenshot of the possibilities here provided as an attachment.

EDIT: ok, I'll try the live usb

---

### Post by amsterdamharu on 2010-12-27
Ok, I think I found the sta driver. You can purge both and then install the broadcom driver:
```

sudo apt-get purge broadcom-sta-common
sudo apt-get purge firmware-b43-installer
sudo apt-get install firmware-b43-installer
```

---

### Post by Rackstar on 2010-12-27
Hi,

I'm on live usb now, so here's what I got. (I'm staying on live usb for the moment)

EDIT: it seems that it's a lucid live usb, my installation is maverick

> sudo lshw -C network
  *-network               
       description: Network controller
**       product: BCM4312 802.11b/g**
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth2
       version: 03
       serial: b8:ac:6f:67:ff:5b
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.0.105 latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:35 ioport:5000(size=256) memory:f0404000-f0404fff(prefetchable) memory:f0400000-f0403fff(prefetchable) memory:f0420000-f043ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 4
       logical name: wlan2
       serial: 70:f1:a1:78:c7:16
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


Here is sudo lspci -n:
> ubuntu@ubuntu:~$ sudo lspci -n
00:00.0 0600: 8086:0044 (rev 12)
00:01.0 0604: 8086:0045 (rev 12)
00:16.0 0780: 8086:3b64 (rev 06)
00:1a.0 0c03: 8086:3b3c (rev 06)
00:1b.0 0403: 8086:3b56 (rev 06)
00:1c.0 0604: 8086:3b42 (rev 06)
00:1c.1 0604: 8086:3b44 (rev 06)
00:1c.3 0604: 8086:3b48 (rev 06)
00:1c.4 0604: 8086:3b4a (rev 06)
00:1c.5 0604: 8086:3b4c (rev 06)
00:1d.0 0c03: 8086:3b34 (rev 06)
00:1e.0 0604: 8086:2448 (rev a6)
00:1f.0 0601: 8086:3b09 (rev 06)
00:1f.2 0106: 8086:3b29 (rev 06)
00:1f.3 0c05: 8086:3b30 (rev 06)
00:1f.6 1180: 8086:3b32 (rev 06)
02:00.0 0300: 1002:68e0
02:00.1 0403: 1002:aa68
**04:00.0 0280: 14e4:4315 (rev 01)**
07:00.0 0805: 1180:e822 (rev 01)
07:00.1 0880: 1180:e230 (rev 01)
07:00.2 0880: 1180:e852 (rev 01)
07:00.3 0c00: 1180:e832 (rev 01)
09:00.0 0200: 10ec:8168 (rev 03)
ff:00.0 0600: 8086:2c62 (rev 02)
ff:00.1 0600: 8086:2d01 (rev 02)
ff:02.0 0600: 8086:2d10 (rev 02)
ff:02.1 0600: 8086:2d11 (rev 02)
ff:02.2 0600: 8086:2d12 (rev 02)
ff:02.3 0600: 8086:2d13 (rev 02)

Again contradiction?

---

### Post by amsterdamharu on 2010-12-27
The package firmware-b43-installer is only available on maverik but the broadcom card would still work in Lucid just with other drivers.

---

### Post by Rackstar on 2010-12-27
> **amsterdamharu said:**
> Ok, I think I found the sta driver. You can purge both and then install the broadcom driver:
```

sudo apt-get purge broadcom-sta-common
sudo apt-get purge firmware-b43-installer
sudo apt-get install firmware-b43-installer
```


Hey, back on my installation, couldn't get the wireless working in live usb too (not able to reboot etc).

I tried the above commands, but nothing changed...

---

### Post by Rackstar on 2010-12-27
I fixed my problem. I was able to install the STA driver through jocky after purging "bcmwl-kernel-source"

However, for installing the STA driver, I tried installing the driver you recommended, but still gave the same error.

I guess maybe I'll just leave it this way and learn to live with my suspend/resume issues. Hopefully it'll be fixed in Natty.

EDIT: Thanks amsterdamharu for all your work! I truly appreciate this

---

### Post by amsterdamharu on 2010-12-27
You can change the live CD to install the drivers but it's a lot of work and it might not work if you use a newer installed version to mod an older ISO (like using maverick to mod a Lucid).
[http://ubuntuforums.org/showthread.php?t=1644967](http://ubuntuforums.org/showthread.php?t=1644967)

After installing the drivers you don't need to reboot but you can give the following commands:[FONT=monospace]
[/FONT]```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
```
[http://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](http://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Rackstar on 2010-12-27
Strange that the wiki says to install bcmwl-kernel-source, while I had to purge it to get my STA driver working.

Anyhow, I'm just glad that it works again! Thanks a million

---

### Post by HeroKing on 2010-12-29
i'm having a similar problem with mine. i tried installing one of the compat-wireless packages so i could try to patch mine for injection, and i ended up killing my driver entirely. now i just get some message saying that the driver is not activated, and when i try to reinstall it, all i get is the "check the jockey.log" file. i already looked at other methods, and none of them worked for me. i'm half tempted to just reinstall ubuntu from scratch here, if that's what's needed to fix my system

---

### Post by Rackstar on 2010-12-29
Hey, 

Sorry to hear that your wireless is also broken. However, maybe it's better if you make a new thread, as this one is marked as "solved", it won't get any attention.

Also, could you provide some more details about your system? like "lspci" and "sudo lshw -C network".

Thanks

---

### Post by HeroKing on 2010-12-29
love to, but it prbly wouldn't be solved as quickly. i'm already set to reinstall, i just need to backup some important stuff first

---

