---
title: "Another Dial Up Catastrophe"
date: 2009-06-10
forum: General Help
---

### Post by da_man2009 on 2009-06-10
I received a copy of Ubuntu Desktop 9.04 today and had the biggest smile on my face. I've heard nothing but good things about this Linux OS and I was very excited to try it out for myself to see what the hype was all about. I must have bad luck, because so I've hit nothing but dead-ends and nothing seems to work properly.

I live in a pretty desolate area where only dial up internet is supported (unfortunately due to my surroundings I can't get a satellite signal). I knew very well going into this project that not all modems were supported by this OS, but I was hopeful when I read some articles about my modem specifically working with Ubuntu.

I'm using an **Agere Systems LT WinModem**.

I wish I were exaggerating, but I've been troubleshooting for nearly 13 hours now trying to get my connection to work. I think I've hit just about every piece of documentation this place has to offer and I've been very unsuccessful connecting to the internet when I know others using the same modem have had success stories.

I'm new to Ubuntu and Linux operating systems in general. Could someone please provide a comprehensive step-by-step guide on configuring my dial up internet connection to work? Linking to guides and documentations is okay, but please know that I've already read a large selection of articles. If there are black and white instructions those would probably be most helpful.

---

### Post by Chronon on 2009-06-10
I suppose you have already read other topics about this, such as: [http://ubuntuforums.org/showthread.php?t=852971](http://ubuntuforums.org/showthread.php?t=852971)

It looks like the last post points to a method of getting it to work.  Good luck!

---

### Post by da_man2009 on 2009-06-10
Yes, I did already try those. Every set of instructions tied to that URL has been unsuccessful in getting my modem to work correctly.

It's upsetting that something which should be so simple can't be achieved with even a mild persistence.

---

### Post by da_man2009 on 2009-06-10
Perhaps this will be of some assistance:

 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.28-11-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009
 scanModem update of:  2009_05_31

The dialer utility package WVDIAL does not appear to be installed on your System. 
Please read Modem/DOCs/wvdial.txt

 There are no blacklisted modem drivers in /etc/modprobe*  files 
 Potentially useful modem drivers now loaded are:
                

Attached USB devices are:
 ID 05e3:0715 Genesys Logic, Inc. USB 2.0 microSD Reader
 ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
If a cellphone is not detected, see [http://ubuntuforums.org/archive/index.php/t-878554.html](http://ubuntuforums.org/archive/index.php/t-878554.html)

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [email]discuss@linmodems.org[/email]

For candidate card in slot 01:09.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 01:09.0	11c1:044c	11c1:044c	Communication controller: Agere Systems LT WinModem 

 Modem interrupt assignment and sharing: 
===================================
 The modem interrupt (IRQ) is 255 . IRQs of 0 or 255 are not functional!! 
 The CPU cannot control the modem until this situation is corrected!!
 Possible corrections are:
   1) Within the boot up BIOS, change from a Windows to a non-PNP/Other Operating System type.
   Instructions for accessing BIOS are at:
      [http://linmodems.technion.ac.il/resources.html](http://linmodems.technion.ac.il/resources.html) within:  Additional Resourcces.
   2a) Add an option "pci=routeirq" to the kernel boot up line.
      Here is an example paragraph from  /boot/grub/menu.lst :
	title           Ubuntu, kernel 2.6.15-26-686
	root            (hd0,6)
	kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda7 ro pci=routeirq
	initrd          /boot/initrd.img-2.6.15-26-686
	savedefault
   2b) Same as above, but use "pollirq" instead of "pci=routeirq". 
   3) Within some BIOS setups, IRQ assignments can be changed.
   4) On non-laptop systems, moving the modem card to another slot has helped.
   5) Sometimes upgrading the kernel changes IRQ assignment.
=====================================

 --- Bootup diagnostics for card in PCI slot 01:09.0 ----
[    0.580300] pci 0000:01:09.0: reg 10 32bit mmio: [0xe6800000-0xe68000ff]
[    0.580308] pci 0000:01:09.0: reg 14 io port: [0xb800-0xb807]
[    0.580315] pci 0000:01:09.0: reg 18 io port: [0xb400-0xb4ff]
[    0.580345] pci 0000:01:09.0: supports D2
[    0.580347] pci 0000:01:09.0: PME# supported from D2 D3hot D3cold
[    0.580352] pci 0000:01:09.0: PME# disabled

 The PCI slot 01:09.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 01:09.0:
	Modem chipset  detected on
NAME="Communication controller: Agere Systems LT WinModem "
CLASS=0780
PCIDEV=11c1:044c
SUBSYS=11c1:044c
IRQ=255
IDENT=Agere.DSP

 For candidate modem in:  01:09.0
   0780 Communication controller: Agere Systems LT WinModem 
      Primary device ID:  11c1:044c
 Support type needed or chipset:	Agere.DSP
 


 The modem has a Lucent/Agere/LSI Mars or Apollo DSP (digital signal processing) chipset. 
Support packages for 2.6.n kernels are at:
 [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/) 
Always use the most update for kernels after 2.6.20, currently martian-full-20080625.tar.gz
For kernels 2.6.20 and less, usr martian-full-20080407.tar.gz.

 See DOCs/AgereDSP.txt for Details.

 At [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/) get the martian-full-20080625.tar.gz and follow Readme-NOW.html
 0x044c -- Mars 3 Perseus data/fax only:North America and Global board
 0x044c -- Mars 3.2 Mercury data fax only when no eeprom is present, North America DAA
-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.3.3
             and the compiler used in kernel assembly: 4.3.3

 The patch utility is needed and is needed for compiling ALSA drivers, and possibly others. 

 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.3
   linuc_headers base folder /lib/modules/2.6.28-11-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-x 1 root dip 277352 2009-02-20 12:25 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by da_man2009 on 2009-06-10
Bump. :)

If there are special bumping rules here, please let me know.

---

### Post by da_man2009 on 2009-06-10
> The modem interrupt (IRQ) is 255 . IRQs of 0 or 255 are not functional!! 
I was able to correct this following step 2a above.

My IRQ is now 21.

---

