---
title: "Broadcom B43 WiFi Drivers"
date: 2011-01-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 'Bohr124365 on 2011-01-06
Hi Guys,

I've recently installed Ubuntu Netbook Edition 10.10 on my Dell Latitude D800. I've managed to get everything working except the Broadcom B43 WiFi drivers. They appear in the proprietary drivers box, but when I active them, I get the error 'SystemError: installArchives() failed'.

Any ideas how to fix this problem?

Cheers,

Tom.

---

### Post by the.scarecrow on 2011-01-06
Can you try connecting to your router with a cable prior to clicking install broadcom drivers. I think the drivers are downloaded from the internet.

---

### Post by 'Bohr124365 on 2011-01-06
Thanks for the reply. I've already connected the laptop to the router, but unfortunately that doesn't solve it. I downloads the drivers and goes to install it, but fails. I've tried installing the b43 installer from Synaptic, but I gets an error and stops that too. Perhaps that's the cause?

---

### Post by ugm6hr on 2011-01-07
Known bug... with solution:
[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

---

### Post by the.scarecrow on 2011-01-07
It look like ugm6hr has found the solution for you.

I recently heard that Broadcom are going to "Open Source" their drivers so perhaps the future looks brighter than has been the case for the past year or so for Broadcom wireless users.

---

### Post by 'Bohr124365 on 2011-01-07
Thanks for your reply. I've given that a shot, but unfortunately it hasn't worked. It went through all the motions, but came up with an error saying something about firmware-b43legacy-installer subprocess returned error exit status 1.

---

### Post by ugm6hr on 2011-01-07
Repeat the process and post the exact output here.
Did wifi work with the LiveCD?

---

### Post by 'Bohr124365 on 2011-01-08
Okay, thanks for your help guys. I've tried it again and here's the whole output. Oh, and it didn't work in the Live CD either :(


> tom@Toms-Laptop:~$ sudo apt-get update
[sudo] password for tom: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release.gpg               
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release.gpg
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_GB
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                   
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_GB
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed Release.gpg [198B]
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed Release [31.4kB]          
Get:5 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,088B]                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main Sources                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/restricted i386 Packages [1,797B]
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/main i386 Packages [28.9kB]
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages [610B]
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/universe i386 Packages [15.5kB]
Fetched 81.0kB in 1s (80.6kB/s)                      
Reading package lists... Done
tom@Toms-Laptop:~$ sudo apt-get --reinstall install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 896kB of archives.
After this operation, 2,597kB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted bcmwl-kernel-source i386 5.60.48.36+bdcom-0ubuntu5 [896kB]
Fetched 896kB in 6s (139kB/s)                                                  
Selecting previously deselected package bcmwl-kernel-source.
(Reading database ... 144614 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) ...
Setting up firmware-b43legacy-installer (4.178.10.4-4) ...
Not supported card here (PCI id 14e4:165
14e4:4324)!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu5) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-24-generic
Building for architecture i686
Building initial module for 2.6.35-24-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-24-generic/updates/dkms/

depmod................

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
Errors were encountered while processing:
 firmware-b43legacy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
tom@Toms-Laptop:~$ ^C
tom@Toms-Laptop:~$ 


---

### Post by ugm6hr on 2011-01-08
Apologies... I assumed your wifi card was supported by that driver - it appears not.
Post the output from:
```
lspci
lshw -class network
```

---

### Post by 'Bohr124365 on 2011-01-08
Thanks again for your help! It says:


> tom@Toms-Laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
tom@Toms-Laptop:~$ lshw -class network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:11:a5:45
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.110 firmware=5705-v3.11 ip=192.168.2.4 latency=32 mingnt=64 multicast=yes
       resources: irq:11 memory:faff0000-faffffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32
       resources: memory:fafec000-fafedfff

---

### Post by peteretep on 2011-01-08
hi guys, I'm having the exact same problem as Tom, thanks for your help so far ugm6hr. hopefully you can finally help us get this sorted.

---

### Post by ugm6hr on 2011-01-09
Unfortunately, you have one of the few Broadcom chipsets that does not play nice with any of the new drivers...
There are reports of it working with STA, but it is intermittent and frustrating for most.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
Feel free to follow the advice here: [http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)
It may identify whether your device is in the list of supported cards, but it will definitely not support 802.11a (i.e. only b/g).

I think ndiswrapper might be an option... Even that doesn't list your device as definitely supported:
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:WORKS](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:WORKS)

Happy to help with further advice, but unless I can find a solution for your specific chipset, it will be a case of trying all options to see what works...

Further links:
[http://johnnydopefish.blogspot.com/2009/02/ubuntu-810-dell-inspiron-5100-broadcom.html](http://johnnydopefish.blogspot.com/2009/02/ubuntu-810-dell-inspiron-5100-broadcom.html)
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/ubuntu-10-10-on-dell-latitude-5100-broadcom-bcm4309-drivers-not-working-848384/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/ubuntu-10-10-on-dell-latitude-5100-broadcom-bcm4309-drivers-not-working-848384/)

---

### Post by 'Bohr124365 on 2011-01-09
Cheers (again) for your help! I've tried the ndiswrapper, but unfortunately it hasn't worked. It seems my chip (Broadcom BCM4309 rev 2) doesn't appear on many sites. I've had a look here ([http://wireless.kernel.org/en/users/Drivers/b43#b43_and_b43legacy](http://wireless.kernel.org/en/users/Drivers/b43#b43_and_b43legacy)), but the chip isn't here. Someone said that Linksys have the same chips, so is it worth trying the Linksys drivers?

---

### Post by peteretep on 2011-01-09
sorry, I just noticed that my system has the BCM4306 rev2 chipset rather than the 4309, is there any hope for me either? I'll check out the links provided too.
ps. have tried just activating the driver under System > Administration > Hardware/Additional Drivers with no luck at all.
thanks, and sorry for jumping on your thread tom, best of luck getting it sorted.

---

### Post by ugm6hr on 2011-01-09
> **tomself1 said:**
> Someone said that Linksys have the same chips, so is it worth trying the Linksys drivers?

Perhaps with ndiswrapper... But I don't know.
The fact that there are no reports of this chipset working with 10.10 does not bode well, I'm afraid...
It may be worthwhile starting a new thread in the networking section with the chipset as title to attract attention.

---

### Post by 'Bohr124365 on 2011-01-10
Thanks for your help ugm6hr! After working through all of the links you posted, the last one actually worked!

If anyone else has the BCM4309 rev 2 card, follow the article here: [http://johnnydopefish.blogspot.com/2009/02/ubuntu-810-dell-inspiron-5100-broadcom.html](http://johnnydopefish.blogspot.com/2009/02/ubuntu-810-dell-inspiron-5100-broadcom.html)

Thanks everyone!

---

### Post by 'Bohr124365 on 2011-01-10
If anyone has any ideas about a graphics problem I'm also suffering from, I'd be very grateful!

[http://ubuntuforums.org/showthread.php?p=10340485#post10340485](http://ubuntuforums.org/showthread.php?p=10340485#post10340485)

---

### Post by fritts on 2011-07-18
I have been reading through alot of these posts and I am still unable to find anything to help my current problem. I have a gateway m675 laptop and I am having issues getting the wireless driver. the OS can see the driver but it displays a message "firmware missing" at this point I was going to search for the driver and reinstall it in hope that it will fix the issue  but since gateway has gone under or just passed all of there support to other companies that now want to charge to download a driver I am coming here. 

I am a newbie to linux, Ubuntu so I am very much in the dark here can anyone help here?

I would really appreciate it.

K Fritts

---

### Post by ugm6hr on 2011-07-18
> **fritts said:**
> I have been reading through alot of these posts and I am still unable to find anything to help my current problem. I have a gateway m675 laptop and I am having issues getting the wireless driver. the OS can see the driver but it displays a message "firmware missing" at this point I was going to search for the driver and reinstall it in hope that it will fix the issue  but since gateway has gone under or just passed all of there support to other companies that now want to charge to download a driver I am coming here. 

I am a newbie to linux, Ubuntu so I am very much in the dark here can anyone help here?

I would really appreciate it.

K Fritts

I would suggest you start a new post in the Beginners section with as much detail as possible.
See the Wifi help link below for the kind of detail that is helpful.
But as a start - if you use an ethernet cable to connect to the internet by wire, often you can activate the correct driver directly from the Hardware Drivers preferences.

---

