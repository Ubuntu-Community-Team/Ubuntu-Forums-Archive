---
title: "Please help me with modem... struggling..."
date: 2006-01-04
forum: Desktop Environments
---

### Post by sbasak on 2006-01-04
Well, typical problem with WinModem....:confused: 

I ran following commands

lspci

------------- result -----------------
[SIZE="2"]0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:07.6 Communication controller: VIA Technologies, Inc. Intel 537 [AC97 Modem] (rev 30)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1420
0000:00:0a.1 CardBus bridge: Texas Instruments PCI1420
0000:00:0e.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0000:00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)[/SIZE]
-------------------------------
Is my modem then AC97?

Next I ran following commands

--------------------- commands -------------
wget -c [http://frankandjacq.com/ubuntuguide/scanModem.gz](http://frankandjacq.com/ubuntuguide/scanModem.gz) 
gunzip -c scanModem.gz > scanModem 
chmod +x scanModem
sudo ./scanModem 
gedit Modem/ModemData.txt
-----------------------------------------------

------------ contents of ModemData.txt file -----------------------

 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 kernel 2.6.12-9-386
 Occassionally reponses are blocked by an Internet Providers mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_April_19
------------ --------------  System information ------------------------
Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-9-386
 The kernel was assembled with compiler:  3.4.5
 a gcc package must be installed to support driver compiling

Checking for kernel-headers needed for compiling.
Kernel-header resources are not evident.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.12-9-386    	[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)
 Ubuntu 		linux-headers-2.6.12-9-386		[http://www.ubuntulinux.org/community/ConfigUbuntu5.04%20repositories](http://www.ubuntulinux.org/community/ConfigUbuntu5.04%20repositories)
    Debian & Ubuntu will also require kernel-kbuild package installation
 Mandrake 	kernel-source-2.6.12-9-386	   If not present on install CDs search
 	[http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/) 
	[http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE		linux-2.6.12-9-386				, ????  , kernels are named k_deflt
One of which must be installed if compiling drivers to match kernel 2.6.12-9-386 proves necessary.
This is necessary for most modem drivers, through some Linux distributions provide some compiled drivers.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
  

 A /dev/modem symbolic link is not set.
 Checking for USB modems
 None found

Modem candidates are at PCI_buses:  0000:00:07.6
    
Providing detail for device at PCI_bus 0000:00:07.6
  with vendor-ID:device-ID
	    ----:----
Class 0780: 1106:3068   Communication controller: VIA Technologies, Inc. Intel 537 [AC97 Modem] (rev 30)
  SubSystem 104d:80f6   Sony Corporation: Unknown device 80f6
0000:00:07.6 0780: 1106:3068 (rev 30)
	Flags: medium devsel, IRQ 5
	I/O ports at 1400 [size=256]
	Capabilities: [d0] Power Management version 2
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 1106:3068 104d:80f6 debian 2.6.12-9-386 3.4.5     i686

       
 The soft modem Subsystem operates under a controller
   1106:3068  VIA 
 capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:

	Pctel
	AgereSystems
	Conexant
	Intel
	Smartlink

	Smartlink software in ALSA mode may support this modem 
 The Subsystem PCI id does not itself identify the modem Codec.
  Driver snd-intel8x0m  may enable codec acquisition 

 Beginning check for older ac97_codec modems.
 An older ac97_modem codec was not detected.

 Checking through information gathered from LinModem ARCHIVES
 From prior reports, the modem codec type of the Subsystem is: CXT
Unknown
 The modem has a Conexant codec: CXT
Unknown
 and there is support for the modem controller: 1106:3068  VIA 
 Some Linux Distributions include the hsfmodem driver.
 Search your packages information for "hsfmodem" and "Conexant".
 If not found there, download a hsfmodem package from [http://www.linuxant.com](http://www.linuxant.com) .
 
 For 2.4.n kernels, If there is not an exact match your kernel version: 2.6.12-9-386
 then kernel-sources must be prepared as described in Modem/DriverCompiling.txt
 before the hsfmodem driver compiling can be successfull. 
 For recent  kernel-source-2.4.6 ,configuration steps are not necessary.
 
	Due to a PCI ID database error, the Intel 537 designation is commonly incorrect.
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 104d is Sony. Subsystem 104d:8129 under a 8086:2486 Intel modem controller
 has a Conexant chip in a Sony Vaio grx560 laptop. 
 A bootup "acpi=on" was required for IRQ acquisition.

 Vendors 127a and 14f1 are Conexant, inheritor of  Rockwell modem  technology. There are also Conexant chipsets
 in some modems from vendors 158b - Allied Data Tech., 1024 - Zenith ,141a - Apache Micro and 148d Digicom Systems.
 With respect to software support there are two main types, hcfpcimodem* and hsfmodem* .
 Download drivers from [http://www.Linuxant.com/drivers/](http://www.Linuxant.com/drivers/)
 
 At   [http://linmodems.technion.ac.il/resources.html#conexant](http://linmodems.technion.ac.il/resources.html#conexant)  , there are scripts aiding installation:
      For HSF modems.
      For HCF modems.
 There is additional Conexant information written to Modem/Conexant.txt 
 
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 1106 is VIA  Technologies Inc.,producing diverse bridges including devices:
    1106:3068    VT82C686/686A/686B AC97 Modem Codec
 Under the later, the  10cf:118e  the "Intel 537" is partially supported
   by the SmartLink slmodem-2.7.10 software
    Subsystem 1102:0033 has an AgereSystems soft modem chip


  ======= PCI_ID checking completed ====== 
 Update=2005_April_19

Analyzing information for PCMCIA device at PCI Bus 00:0a.0
GREPping for an inserted PCMCIA modem with filter:        ommunication

Analyzing information for PCMCIA device at PCI Bus 00:0a.1
GREPping for an inserted PCMCIA modem with filter:        ommunication
 A PCMCIA modem is detected.
      
 The stardard ltmodem resources should suffice for modem support:
     [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
 if the modem has a Lucent/Agere digital processing chipset.
 
GCCversion=
   
For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant modems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for Lucent/Agere DSP modems
   
The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe_mppc
-------------------------------------
 Resident PPP support modules are properly uncompressed .
----active COMM services are ------------
eth0      Link encap:Ethernet  HWaddr 08:00:46:90:92:D1  
          inet6 addr: fe80::a00:46ff:fe90:92d1/64 Scope:Link
This COMM mode should be closed before using the modem, or DNS services may fail.
Be sure to read the section about ppp related modules and aliases in Modem/General.txt
 Be sure to read the Ethernet section of Modem/General.txt 
DEVPPP=crw------- 1 root root 108, 0 2006-01-03 18:59 /dev/ppp
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
  debian is not yet providing pre-compiled drivers for WinModems


-----------------------------------


Any idea where do I go now???

---

### Post by edemark on 2006-01-05
OK so without being a great guru of linux i would suggest you the following:
make right click with your mous on all links in your own post linmodems.technion.ac.il on linuxant.com and even on ltmodem.heby.de you may never know which will help ypu. On the second place i may assueme that you are using a sony viao so i might suggest that you rush against google with the type of your machin ( ej linux on sony viao XXZZ11) pls change XXZZ11 with your machins number. If it was a laptop you may refer to the following site (use google again) linux on laptops it may help

Finally without being someone who knows i would suggest you to check out linuxant page

good luck 
if any comment than write but before that search and read

---

### Post by L Campbell on 2006-01-05
>>>>
------------ contents of ModemData.txt file -----------------------

DO use the following line as the email Subject Line, to alert cogent experts:
scanModem, Ubuntu 5.10 kernel 2.6.12-9-386
Occassionally reponses are blocked by an Internet Providers mail filters.
So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on: 2005_April_19
<<<<<<<<<<<

If you haven't already followed these instructions you might want to do so.

The people at ' [www.linmodems.org](www.linmodems.org) ' are very knowledgeable and will be able to help you.

Good luck.

---

### Post by stratotak on 2006-01-05
you can also go to   [http://www.linux-laptop.net/](http://www.linux-laptop.net/)     and see if your laptop is listed..and see if someone has modem setup to work...

---

