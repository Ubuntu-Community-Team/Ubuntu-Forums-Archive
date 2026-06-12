---
title: "will beryl work for me?"
date: 2007-03-15
forum: Desktop Effects &amp; Customization
---

### Post by da1nonlymikeo on 2007-03-15
hey quick question. do i need to build compiz to install beryl? or can i get beryl on my stock ubuntu 6.10 settup?

if needed are there any walkthroughs on how to setup compiz on a hp pavilion dv6000?

---

### Post by irwa82 on 2007-03-15
Hi,

I use beryl on my computer and did not compile a thing to get it working. Check out this site [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu) for instructions on how to get it running.

---

### Post by da1nonlymikeo on 2007-03-15
Ubuntu 6.10 (Edgy Eft)

    * Graphic Card Drivers
    * Install Beryl on Ubuntu Edgy with XGL
    * Install Beryl on Ubuntu Edgy with AIGLX
    * Install Beryl on Ubuntu Edgy with nVidia (1.9xxx or higher)
    * Install Beryl on Ubuntu Edgy with XGL and ATI (Automatic installation)

 eh wich one should i install?

---

### Post by irwa82 on 2007-03-15
Hi,

You will want the aiglx option but you will also need to make sure that your graphics card is configured.

before you do you need to make sure that your card supports direct rendering. to do that follow below step.

glxinfo|grep -i 'direct rendering'
direct rendering: Yes

if the output is not yes then you will need to configure your graphics card. To find out what type of graphics card you have do the below step.

/sbin/lspci

then look through the list to find out what graphics card you have and look in the graphics drivers page on the beryl site for configuring your graphics card.

---

### Post by da1nonlymikeo on 2007-03-15
mike@mike-laptop:~$ glxinfo|grep -i 'direct rendering'
libGL warning: 3D driver claims to not support visual 0x5b
direct rendering: Yes




mike@mike-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
05:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 02)

---

### Post by irwa82 on 2007-03-15
Hi,

You should not have any problems from what I can see your setup should work out of the box.

go here [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX) and follow the instructions.

---

### Post by bb05 on 2007-03-20
edit: direct was a no. :( 

00:00.0 Host bridge: ATI Technologies Inc Unknown device 7831
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP PCI/AGP Bridge
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 1a)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
1:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 9200 IGP
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)


what would i need to do to get this working with a nubuntu livecd / install ?

thx in adv. :D

---

### Post by da1nonlymikeo on 2007-03-22
works great! thanks irwa:)

---

