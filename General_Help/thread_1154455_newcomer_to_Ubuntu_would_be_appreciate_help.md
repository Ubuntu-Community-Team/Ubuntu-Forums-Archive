---
title: "newcomer to Ubuntu would be appreciate help"
date: 2009-05-09
forum: General Help
---

### Post by n.hinton on 2009-05-09
New and first time install of ubuntu (ver 9.04) used CD to repartition and install on HD – Wow so easy and impressive – everything old windows and new ubuntu all work great. Set the login option as automatic (only user).

First prob with ubuntu is modem support. – read some support docs and subsequently downloaded (with windows) slmodem-2.9.11-20080126.tar.gz and ungrab-winmodem-20070505.tar.gz plus scanModem.gz

Read the instructions, did the scan, did the correct make clean make install in the makefile directory extracted from the archive. But don’t know how to determine if the modem is correctly installed and functioning. I see in 9.04’s docs that the network manager doesn’t support dial up and would need a support package downloaded (at this point I am getting a little irritated). How do I get a network manager that supports dial-up?

Read a bit more totally alien Ubuntu/linux stuff and tried to edit /etc/default/sl-modem-daemon entry, 

FORCESTART=0
To
FORCESTART=1

Thought it worth a try. G-edit will not let me save changes, says don’t have permission.

As I said before I am set up as the only user, have run the root terminal thing giving my password,  ‘made no difference’ tried logging on as root and giving the only password that this new installation has ever seen and it said it’s the wrong password! (Nothing entered also failed for root)

As a complete newcomer to Ubuntu I would be appreciative of any help the forum can supply.

Don’t know if the following paste ‘s are of any use, but here anyway:


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
 scanModem update of:  2008_11_06
The modem symbolic link is /dev/modem -> ttySL0
 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 0d49:3200 Maxtor 
 ID 03f0:0604 Hewlett-Packard DeskJet 840c
 ID 045e:001e Microsoft Corp. IntelliMouse Explorer
 ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
 ID 1d6b:0001 Linux Foundation 1.1 root hub

USB modems not recognized

For candidate card in slot 00:08.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:08.0	10b9:5459	10a5:5459	Modem: ALi Corporation SmartLink SmartPCI561 56K Modem

 Modem interrupt assignment and sharing: 
 --- Bootup diagnostics for card in PCI slot 00:08.0 ----
[    1.338174] pci 0000:00:08.0: reg 10 32bit mmio: [0xeffff000-0xefffffff]
[    1.338185] pci 0000:00:08.0: reg 14 io port: [0xdc00-0xdcff]
[    1.338218] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    1.338227] pci 0000:00:08.0: PME# disabled
[    3.265064] serial 0000:00:08.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    3.265659] 0000:00:08.0: ttyS2 at I/O 0xdc28 (irq = 10) is a 8250
[    3.265932] 0000:00:08.0: ttyS3 at I/O 0xdc40 (irq = 10) is a 8250
[    3.265977] Couldn't register serial port 0000:00:08.0: -28
[   33.742214] serial 0000:00:08.0: PCI INT A disabled

 The PCI slot 00:08.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:08.0:
	Modem chipset  detected on
NAME="Modem: ALi Corporation SmartLink SmartPCI561 56K Modem"
CLASS=0703
PCIDEV=10b9:5459
SUBSYS=10a5:5459
IRQ=10
IDENT=slamr

 For candidate modem in:  00:08.0
   0703 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
      Primary device ID:  10b9:5459
 Support type needed or chipset:	slamr
 

----------------end Softmodem section --------------
The modem is supported by the Smartlink 
plus the slmodemd helper utility.  Read the
DOCs/Smartlink.txt and Modem/DOCs/YourSystem.txt for follow through guidance.


For 2.6.28-11-generic compiling drivers is necessary. As of October 2007 the current packages at
[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)  are the
ungrab-winmodem-20070505.tar.gz and slmodem-2.9.11-20080126.tar.gz

Writing DOCs/Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.3.3
             and the compiler used in kernel assembly: 4.3.3


 
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


 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

# start/stop the daemon when the USB modem is connected
KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   lrwxrwxrwx 1 root root 6 2009-05-08 23:56 /dev/modem -> ttySL0
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/030_sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/rules.d/030_sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
/etc/udev/sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/sl-modem-daemon.modutils:install slamr modprobe --ignore-install ungrab-winmodem ;  modprobe --ignore-install slamr; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0) 
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by dcstar on 2009-05-09
> **n.hinton said:**
> 
........
Read a bit more totally alien Ubuntu/linux stuff and tried to edit /etc/default/sl-modem-daemon entry, 

FORCESTART=0
To
FORCESTART=1

Thought it worth a try. G-edit will not let me save changes, says don’t have permission.
.......
```

sudo gedit whatever
```

---

