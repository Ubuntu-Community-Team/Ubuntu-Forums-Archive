---
title: "errors installing modem driver"
date: 2006-04-07
forum: Desktop Environments
---

### Post by whoa_551 on 2006-04-07
I am trying to install the slmodem driver for my SmartLink56k internal modem on my laptop in Ubuntu.  However, I get the following error messages, and nothing ends up getting installed:

```
~/smartlink/slmodem-2.9.10$ sudo make
make -C modem all
make[1]: Entering directory `/home/wateroot/smartlink/slmodem-2.9.10/modem'
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem.o -c modem.c
modem.c: In function "modem_reset":
modem.c:1701: error: invalid storage class for function "sregs_init"
modem.c:1713: warning: implicit declaration of function "sregs_init"
modem.c: At top level:
modem.c:1727: error: static declaration of "sregs_init" follows non-static declaration
modem.c:1713: error: previous implicit declaration of "sregs_init" was here
make[1]: *** [modem.o] Error 1
make[1]: Leaving directory `/home/wateroot/smartlink/slmodem-2.9.10/modem'
make: *** [modem] Error 2
wateroot@workstation:~/smartlink/slmodem-2.9.10$ make install
make -C modem all
make[1]: Entering directory `/home/wateroot/smartlink/slmodem-2.9.10/modem'
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem.o -c modem.c
modem.c: In function "modem_reset":
modem.c:1701: error: invalid storage class for function "sregs_init"
modem.c:1713: warning: implicit declaration of function "sregs_init"
modem.c: At top level:
modem.c:1727: error: static declaration of "sregs_init" follows non-static declaration
modem.c:1713: error: previous implicit declaration of "sregs_init" was here
make[1]: *** [modem.o] Error 1
make[1]: Leaving directory `/home/wateroot/smartlink/slmodem-2.9.10/modem'
make: *** [modem] Error 2
wateroot@workstation:~/smartlink/slmodem-2.9.10$
```

Any ideas what the problem could be?

---

### Post by towsonu2003 on 2006-04-14
for make install to work, make has to exit without errors... 

is this the sl-modem-source package from ubuntu's repositories? you could also try the precompiled slmodem from linmodems.org (let me know if you need more info, and attach your modemdata.txt). 

also, check out second link in my signature, if you didn't do so already. it has a sections for scanmodem (hence modemdata.txt) and slmodems.

---

### Post by winkshog on 2006-04-18
I am getting the same problem with my modem.
This is the error I am getting

make -C modem all
make[1]: Entering directory `/opt/slmodem-2.9.10/modem'
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem.o -c modem.c
modem.c: In function &#8216;modem_reset&#8217;:
modem.c:1701: error: invalid storage class for function &#8216;sregs_init&#8217;
modem.c:1713: warning: implicit declaration of function &#8216;sregs_init&#8217;
modem.c: At top level:
modem.c:1727: error: static declaration of &#8216;sregs_init&#8217; follows non-static declaration
modem.c:1713: error: previous implicit declaration of &#8216;sregs_init&#8217; was here
make[1]: *** [modem.o] Error 1
make[1]: Leaving directory `/opt/slmodem-2.9.10/modem'
make: *** [modem] Error 2
linux:/opt/slmodem-2.9.10 #

you asked about this file info


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, 
Welcome to SUSE LINUX 10.0 (i586) - Kernel  kernel 2.6.13-15.8-default  
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2006_April_07
------------ --------------  System information ------------------------
 
Welcome to SUSE LINUX 10.0 (i586) - Kernel 
 on System with processor: i686
 currently under kernel:   2.6.13-15.8-default
 Be sure to read the Ethernet section of Modem/YourSystem.txt 

  The current modem symbolic link is: /dev/modem -> /dev/ttyS0
  The ports /dev/ttyS0 or 1,2,3 are for standard Controller chip modems

 USB modem not detected.

 Checking for audio card 
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
	Reading /proc/asound/pcm 
00-00: Intel ICH : Intel 82801BA-ICH2 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801BA-ICH2 - MIC ADC : capture 1
 The potentially supporting drivers now loaded on this System are:
0 snd_intel8x0


 The kernel was assembled with compiler:  4.0.2
 with current System compiler GCC=4.0.2
-------------
 Found make utility.
-------------
Checking for kernel-headers needed for compiling.
 Kernel-header resources needed for compiling are not manifestly ready!

Modem candidates are at PCI_buses:  02:0a.0
    
Providing detail for device at  02:0a.0
  with vendor-ID:device-ID
	    ----:----
Class 0703: 2000:2800   Modem: Smart Link Ltd.: Unknown device 2800 (rev 02) (prog-if 00 [Generic])
  SubSystem 163c:2800  Smart Link Ltd.: Unknown device 2800
	Flags: medium devsel, IRQ 11
 Checking for IRQ 11 sharing with modem.
      XT-PIC  eth0

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 2000:2800 163c:2800 SuSE 2.6.13-15.8-default  4.0.2 4.0.2    i686

The SmartLink slamr driver supports this modem:
    2000:2800  Gateway SL2800
complemented by the SmartLink slmodemd.

 == Checking PCI IDs through modem chip suppliers ==

 SmartLink at [http://www.smlink.com/](http://www.smlink.com/) owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  [http://www.smlink.com/main/index1.php?ln=en&main_id=40](http://www.smlink.com/main/index1.php?ln=en&main_id=40)
 But a more recent code and a much broader license for other chipset support,
 can be downloaded from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)  
 Though not always needed, download the files: 
   slmodem-CurrentVersion.tar.gz - provides the most general code package.
   SLMODEMD.gcc4 - provides a compiled slmodemd 
   ungrab-winmodem.tar.gz  -  may be needed for usage with slamr. 
 Details on their usage are in Slmodem.txt, Slmodem-ALSA.txt and
 [http://linmodems.technion.ac.il/slmodem-serial.html](http://linmodems.technion.ac.il/slmodem-serial.html)


  ======= PCI_ID checking completed ====== 
 Update=2006_April_07
A PCMCIA CardBus is not detected on this System.
drwxr-xr-x  2 root root 560 2006-04-15 14:53 /dev/.udevdb

There is an active UDEV file system, creating device nodes in volatile RAM.
For SmartLink modems using the slamr.ko or slusb.ko drivers an /etc/init.d/ script
will be necessary to create /dev/slamr0 or /dev/slusb0 ports, or manually by:
#  mknod -m 600 /dev/slamr0 c 242 0
#  mknod -m 600 /dev/slusb0 c 243 0
upon each bootup.

For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant modems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for Lucent/Agere DSP modems
   
 Checking for modem symbolic link support lines within /etc/udev/ files


 The kernel-2.6.13-15.8-default was compiled with CONFIG_REGPARM, providing more compact and faster code.


 dequate match of gcc versions of the compiler and kernel.
Kernel-header resources needed for compiling are not manifestly ready!
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.13-15.8-default    	[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) or install CD
 Ubuntu 		linux-headers-2.6.13-15.8-default		[http://http://packages.ubuntu.com/](http://http://packages.ubuntu.com/) or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.13-15.8-default	   If not present on install CDs search
 	[http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/) 
	[http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE		kernel-source-2.6.13-15.8-default		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.13-15.8-default or kernel-smp-devel-2.6.13-15.8-default on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.13-15.8-default proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

 Modem symbolic link is:  /dev/modem -> /dev/ttyS0

The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.conf:# ppp over ethernet
/etc/modprobe.conf:# the kernel 2.2 uses pppox
/etc/modprobe.conf:# the kernel 2.4 uses pppoe
/etc/modprobe.conf:alias char-major-108      ppp_generic
/etc/modprobe.conf:alias char-major-144      pppoe
/etc/modprobe.conf:alias net-pf-24           pppoe
/etc/modprobe.conf:# the kernel 2.2 uses ppp.o as ppp driver,
/etc/modprobe.conf:# the kernel 2.4 uses ppp_generic.o
/etc/modprobe.conf:alias ppp0                ppp_generic
/etc/modprobe.conf:alias ppp1                ppp_generic
/etc/modprobe.conf:alias tty-ldisc-3         ppp_async
/etc/modprobe.conf:alias ppp-compress-18          ppp_mppe
/etc/modprobe.conf:alias ppp-compress-21          bsd_comp
/etc/modprobe.conf:alias ppp-compress-24          ppp_deflate
/etc/modprobe.conf:alias ppp-compress-26          ppp_deflate
-------------------------------------
 Resident PPP support modules are properly uncompressed .
----active COMM services are ------------
eth0      Link encap:Ethernet  HWaddr 00:03:47:C4:F2:D8  
          inet6 addr: fe80::203:47ff:fec4:f2d8/64 Scope:Link
This COMM mode should be closed before using the modem, or DNS services may fail.
 ---- dmesg queries -------
ACPI: local apic disabled
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
  IO window: disabled.
apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac)
apm: overridden by ACPI.
audit: initializing netlink socket (disabled)
ACPI: PCI interrupt for device 0000:02:0a.0 disabled
pnp: Device 00:08 disabled.
pnp: Device 00:08 disabled.
pnp: Device 00:08 disabled.

  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the [http://www.smlink.com](http://www.smlink.com)  slmodem software.
  Check pppd version with:
    pppd --version
  See  [http://linmodems.technion.ac.il/archive-fourth/msg03167.html](http://linmodems.technion.ac.il/archive-fourth/msg03167.html)
    

 The following packages should be installed to support compiling and modem testing:
  make, glibc-devel, gcc-3.3 , libasound2-dev, wvdial and kernel-source-2.6.13-15.8-default 
  SuSE 9.0 and later has pre-compiled drivers supporting the following modem chipsets:
     Intel HaM and 536ep
     Conexant HSF (but not the HCF)
     Lucent/AgereSystems ltmodem (Digital Siggnal Processing type)
     IBM wmave
     Smart Link soft modems
  Unfortunately only the  Intel HaM and 536ep are on the  3 CD Personal set, pending an update.
  Locations on the 6 CD Professional set are:
     CD4/suse/i586/smartlink-softmodem-2.7.9-89.i586.rpm  - the slmodemd daemon
     CD3/suse/i586/km_smartlink-softmodem-2.7.9-89.i586.rpm - slmodem driver compiling
     CD4/suse/i586/hsfmodem-5.03.27mbsibeta02122600-92.i586.rpm - softmodem configuration
     CD4/suse/i586/km_hsfmodem-5.03.27mbsibeta02122600-92.i586.rpm -softmodem driver code
        installation report -  [http://linmodems.technion.ac.il/archive-fourth/msg00350.html](http://linmodems.technion.ac.il/archive-fourth/msg00350.html)
     CD4/suse/i586/ltmodem-8.26a-54.i586.rpm - a patch from SuSE may be needed for function
        installation report - [http://linmodems.technion.ac.il/archive-fourth/msg00458.html](http://linmodems.technion.ac.il/archive-fourth/msg00458.html)
     CD4/suse/i586/Intel-536ep-4.51-200.i586.rpm
     CD4/suse/i586/Intel-v92ham-4.51-244.i586.rpm
     CD4/suse/i586/mwavem-1.0.4-110.i586.rpm
Some pre-compiled SuSE 9.0 packages for the 2.4.21-99-default kernel are available at:
      [http://linmodems.technion.ac.il/packages/SuSE-9.0/](http://linmodems.technion.ac.il/packages/SuSE-9.0/)
  including AgereSoftModem and the Intel537 modems

  IMPORTANT - The kernel-source-144/README.SuSE informs that the pre-assembled kernel-headers installed
  from the 9.0 kernel-source-99 have some flaws.  Upgrading to a later kernel, such as 2.4.21-144 with matching kernel-source is the simplest may of avoiding problems.
  
  SuSE 9.1 comes with a SmartLink slamr.ko driver installed,
  aiding identification of softmodem codecs by:
    dmesg | grep slamr
 
  For the 9.1 Personal (single CD installation) winmodem packages
  have be downloaded from the SuSE 9.1 repository
  Should compiling drivers may be necessary,  the following additional packages
  will have to be downloaded and installed:
  	make, glibc-devel, gcc-3.3.3 and kernel-source.
  The kernel-headers are co-installed with the kernel-source.
  Thus subsequent driver compiling does Not require additional preparations.
    
any help wold be great

---

### Post by towsonu2003 on 2006-04-18
unfortunately I don't know what the compilation errors are. make sure you have build-essential and linux-headers packages. 

for that, put install CD, mount it, 
```

sudo apt-get update
sudo apt-get install build-essential linux-headers-`uname -r`

```

also try using gcc-3.4 (see dialup wiki on how to download it) with 
CC=gcc-3.4 make -C modem all

if these don't work, try to use the precompiled slmodem deamon: See instructions here: [http://ubuntuforums.org/showpost.php?p=925357&postcount=2](http://ubuntuforums.org/showpost.php?p=925357&postcount=2) but change "snd_ali5451" in that post with your own module (snd-intel8x0m).

one note: are you trying to install the slmodem under suse? if not, run scanmodem again under ubuntu to see if it gives you some advice on how to compile and stuff...

---

