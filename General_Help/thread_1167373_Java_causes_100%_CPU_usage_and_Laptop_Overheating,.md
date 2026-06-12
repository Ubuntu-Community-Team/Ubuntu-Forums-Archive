---
title: "Java causes 100% CPU usage and Laptop Overheating, FF related"
date: 2009-05-22
forum: General Help
---

### Post by Shekibobo on 2009-05-22
Hey, all!

I've recently observed a problem with using Java in FF3.0.1.0.  Specifically, but not exclusively, when running yahoo games, my applets don't finish loading, and my CPU usage jumps up near 100%.  My computer heats up to at least 85*C, which seems to be the highest temperature my sensors will read.  I saw another post with this problem, but it was never solved, and it was years old.  When I go into system monitor, Java is the only thing using cpu, and I have to kill the process to make things work normally again.  Even after killing Firefox, java keeps running and overheating things.  Sometimes it won't even let me kill it.  

The following java packages are installed according to Synaptic:

sun-java6-bin
ia32-sun-java6-bin
sun-java6-jre
sun-java6-plugin
sun-java6-jdk

ia32-sun-java6-bin was installed as an alternative to java, which I have running on 64bit ubuntu 9.04, mainly to get Juniper Network Connect running for my school.

I've only recently noticed this problem being related to java, and I'm not sure how long it's been going on.  The first time I noticed it, it was not caused by yahoo games, but possibly some other website with games or videos using java.  And sometimes it doesn't get out of control.  But as soon as it starts like that, it won't quit until I kill it or reboot.  And it causes my computer to heat up well beyond it's safe operating temperature, even if I let it sit.  Does anyone else have this problem?  Or a fix?

Thanks, everyone for your help!

Since it seemed to be a theme of the other post I found, I am including the java-related information from about:plugins for Firefox:

**IcedTea Java Web Browser Plugin**

 File name:  IcedTeaPlugin.so The IcedTea Java Web Browser Plugin 1.4.1 (6b14-1.4.1-0ubuntu7) executes Java applets.
 MIME Type Description Suffixes Enabled    
application/x-java-vm IcedTea class,jar Yes 
  application/x-java-applet IcedTea class,jar Yes 
  application/x-java-applet;version=1.1 IcedTea class,jar Yes
 application/x-java-applet;version=1.1.1 IcedTea class,jar Yes
 application/x-java-applet;version=1.1.2 IcedTea class,jar Yes
 application/x-java-applet;version=1.1.3 IcedTea class,jar Yes   
application/x-java-applet;version=1.2 IcedTea class,jar Yes   
application/x-java-applet;version=1.2.1 IcedTea class,jar Yes 
  application/x-java-applet;version=1.2.2 IcedTea class,jar Yes   
application/x-java-applet;version=1.3 IcedTea class,jar Yes 
  application/x-java-applet;version=1.3.1 IcedTea class,jar Yes 
  application/x-java-applet;version=1.4 IcedTea class,jar Yes   
application/x-java-applet;version=1.4.1 IcedTea class,jar Yes   
application/x-java-applet;version=1.4.2 IcedTea class,jar Yes 
  application/x-java-applet;version=1.5 IcedTea class,jar Yes 
  application/x-java-applet;version=1.6 IcedTea class,jar Yes   
application/x-java-applet;jpi-version=1.6.0_00 IcedTea class,jar Yes 
  application/x-java-bean IcedTea class,jar Yes
 application/x-java-bean;version=1.1 IcedTea class,jar Yes
 application/x-java-bean;version=1.1.1 IcedTea class,jar Yes   
application/x-java-bean;version=1.1.2 IcedTea class,jar Yes
 application/x-java-bean;version=1.1.3 IcedTea class,jar Yes   
application/x-java-bean;version=1.2 IcedTea class,jar Yes 
  application/x-java-bean;version=1.2.1 IcedTea class,jar Yes 
  application/x-java-bean;version=1.2.2 IcedTea class,jar Yes   
application/x-java-bean;version=1.3 IcedTea class,jar Yes
 application/x-java-bean;version=1.3.1 IcedTea class,jar Yes
 application/x-java-bean;version=1.4 IcedTea class,jar Yes 
  application/x-java-bean;version=1.4.1 IcedTea class,jar Yes
 application/x-java-bean;version=1.4.2 IcedTea class,jar Yes
 application/x-java-bean;version=1.5 IcedTea class,jar Yes
 application/x-java-bean;version=1.6 IcedTea class,jar Yes
 application/x-java-bean;jpi-version=1.6.0_00 IcedTea class,jar Yes

Hope we can all figure this out together.

---

### Post by random_hypocrisy on 2009-05-22
Run this in Terminal;

**lspci**

And copy and paste the result back here.

---

### Post by Shekibobo on 2009-05-23
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by Yellow Pasque on 2009-05-23
Your browser is using the IcedTea plugin (icedtea6-plugin), not the actual Sun Java plugin. Close all FF windows and try making the sun-java6-plugin the default with this command:

```
sudo update-alternatives --config xulrunner-1.9-javaplugin.so
```

Start FF and verify that the Sun plugin is being used in about:plugins . See if the CPU usage issue is still present.

BTW, make sure the air vents aren't blocked or dust-clogged. A CPU really shouldn't overheat just from an extended load. (Unfortunately, laptop cooling systems are often inadequate.) Also, see if there's an automatic shutdown on overheat option in your BIOS.

---

### Post by Shekibobo on 2009-05-23
Thanks, that definitely took care of it.  Yay, TextTwist!

---

### Post by uiberto on 2009-05-29
Thanks. I had the same issue and your advice fixed it.

---

### Post by weremichael on 2009-05-30
This fixed the problem for me too. Thanks.

---

