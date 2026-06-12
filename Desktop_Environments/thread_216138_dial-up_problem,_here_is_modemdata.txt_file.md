---
title: "dial-up problem, here is modemdata.txt file"
date: 2006-07-15
forum: Desktop Environments
---

### Post by Fittersman on 2006-07-15
```


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 6.06 LTS  kernel 2.6.15-23-386  
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at DISCUSS@linmodems.org
Code updated on:  2006_July_01
------------ --------------  System information ------------------------
 Ubuntu 6.06 LTS 
 on System with processor: i686
 currently under kernel:   2.6.15-23-386

 https://wiki.ubuntu.com/DialupModemHowto has good general guidance.
 Be sure to read the Ethernet section of Modem/YourSystem.txt 
DEVPPP=crw------- 1 root root 108, 0 2006-05-30 19:15 /dev/ppp
A /dev/modem symbolic link is not present
 USB modem not detected.

 Checking for audio card 
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Reading /proc/asound/pcm 
00-00: Intel ICH : Intel 82801DB-ICH4 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801DB-ICH4 - MIC ADC : capture 1
00-02: Intel ICH - MIC2 ADC : Intel 82801DB-ICH4 - MIC2 ADC : capture 1
00-03: Intel ICH - ADC2 : Intel 82801DB-ICH4 - ADC2 : capture 1
00-04: Intel ICH - IEC958 : Intel 82801DB-ICH4 - IEC958 : playback 1
 The potentially supporting drivers now loaded on this System are:
0 snd_intel8x0


 The kernel was assembled with compiler:  4.0.3
 a gcc-4.0.3  package must be installed to support driver compiling
-------------
 Compiling utility   make   Not found.
-------------
Checking for kernel-headers needed for compiling.
 Kernel-header resources needed for compiling are not manifestly ready!

Modem candidates are at PCI_buses:  0000:01:0b.0
    
Providing detail for device at  0000:01:0b.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 11c1:044c   Communication controller: Agere Systems LT WinModem (rev 02)
  SubSystem 11c1:044c  Agere Systems LT WinModem
	Flags: bus master, medium devsel, latency 64, IRQ 201
 Checking for IRQ 201 sharing with modem.
O-APIC-level  ehci_hcd:usb4

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:044c 11c1:044c debian_version 2.6.15-23-386  4.0.3 none    i686
 == Checking PCI IDs through modem chip suppliers ==
	  
 The modem has a supported Lucent/Agere DSP (digital signal processing) Mars or Apollo DSP
 (digital signal processing) chipset with primary PCI_ID:  11c1:044c
 DSP=1

Support packages for 2.6.n kernels are at:
http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/ with folders for
	debian/  containing some installers
	ubuntu/  containing some installers
The ltmodem-8.26b1.tar.gz  and ltmodem-8.31b1.tar.gz are driver compiling resources,
with the 8.31 having support for SMP (symmetric multi processor) motherboards.
These packages are more automated versions of the ltmodem-2.6-alk* packages
The ltmodem-2.6-Nalk.src.rpm packages can be used with rpm using Distros.
	   # rpmbuild --rebuild ltmodem-2.6-Nalk.src.rpm  
	   will deposit an installer at:
	        /usr/src/rpm/RPMS/i686/ltmodem-kv_2.6.15-23-386.rpm 	   Check with  
            # ls -l   /usr/src/rpm/RPMS/i686/ltmodem*
	    Then install with:
	    # rpm -i /usr/src/rpm/RPMS/i686/ltmodem-kv_2.6.15-23-386.rpm
	    or similar.

The martian.tar.gz represents a new developmental track, meeting emerging kernel requirements.
See for details:  http://martian.barrelsoutofbond.org/
http://linmodems.technion.ac.il/archive-sixth/msg00142.html
AMD x86_64 competency is provided only bt the martian.

For 2.4.n kernels packages are at http://ltmodem.heby.de/ or http://phep2.technion.ac.il/linmodems/packages/ltmodem/

 There are some installer packages and also resources for compiling drivers.
 ----------------------
 SuSE/Novell Linux and some other Distros provide compiled drivers +installers.
    Search package lists for ltmodem  
 For other Distros and 2.6.n kernels, see: 

 Packages for compiling drivers are:
 ResourceName                Use for kernel ranges
--------------------------------------------------------------------------------
ltmodem-8.26a.tar.gz         2.4.21 and earlier
ltmodem-8.30a3.tar.gz        2.4.21 and subsequent 2.4.2n kernels
	    which were assembled with a gcc-2.9 comiler
ltmodem-8.31a10.tar.gz     beginning with 2.4.21 and upto about 2.6.8  kernels
martian.tar.gz             2.6.n SMP (symmetic multiprocessor) support not verified.
ltmodem-8.31b1.tar.gz      2.6.n with    SMP support, for some* Systems
ltmodem-8.26b1tar.gz       2.6.n without SMP support
   * While SMP capacity should in principle be without ill effect on single processor systems,
the are some cases of ill effects on single processor systems.

Some additional 2.4.n installers are available from:
http://dag.wieers.com/packages/kernel-module-ltmodem/ for some other 2.4.n installers.


 Vendor 11c1 corresponds to Lucent Technologies or subsidiary Agere Systems, Inc.
 Information is at:  http://www.agere.com/client/modem_dsp.html. Produced are both:
   1) modems identifiable from their primary PCI IDs and 
   2) soft modem Subystem chips requiring identification through codec readouts.
   
 Lucent/Agere Mars/WinModem drivers from version 8.30 onwards have
 the necessary fix for SMP machines which includes machines with
 hyperthreading turned on (virtually acting as two CPUs).
 
 Call waiting specified by, +pcw=1, is not implmented in the ltmodem drivers.
Configuration with forcing is described in: http://linmodems.technion.ac.il/archive-fifth/msg00055.html
 0x044c -- Mars 3 Perseus data/fax only:North America and Global board
 0x044c -- Mars 3.2 Mercury data fax only when no eeprom is present, North America DAA


  The desired installer name is like:
========================================
ltmodem-2.6.15-23-386_8.nn_i386.deb
----------------------------------------
 ltmodem-kv-Kernel_FL-LTver--.CPU.rpm   explains the versioning.
 For your System
            Kernel_FL is 2.6.15-23-386 , the full kernel version displayed by: uname -r
                      LTver is 8.31b1, the release of the compiler kit
                               8.nn is the Agere core code designation.
       The proccesor type or CPU is:  i686      dispayed by:  uname -m
 used in compiling and assembling driver packages.

      
 A suitable installer is not available as of this 2006_July_01 update.
 Check in the section debian_version at  http://ltmodem.heby.de/
   for a subsequent Installer submission.
 Older releases have been archived at:
   http://linmodems.technion.ac.il/packages/ltmodem/archive/
 Also there is a RPM search engine at:   http://rpm.pbone.net
 The closest match to your   i686=CPU   is recommended.
   The closest match to your   i686=CPU   is recommended.
   For example replacements in order of preference for an
     i686 would be i586, i486 and i386
 If not present use the  ltmodem-8.31b1.tar.gz compiler kit.

 The list of available Installers for debian_version as of this 2006_July_01
 is inserted into to Modem/YourSystem.txt
  ======= PCI_ID checking completed ====== 
 Update=2006_July_01
A PCMCIA CardBus is not detected on this System.
 Checking for modem symbolic link support lines within /etc/udev/ files


Checking the /etc/apt/sources.list

deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted



deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling


      
 The Major.Minor versions differ in the designated compiler none and the 4.0.3 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See http://linmodems.technion.ac.il/archive-fifth/msg04252.html 
 
Kernel-header resources needed for compiling are not manifestly ready!
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.15-23-386    	http://www.debian.org/distrib/packages or install CD
 Ubuntu 		linux-headers-2.6.15-23-386		http://http://packages.ubuntu.com/ or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.15-23-386	   If not present on install CDs search
 	http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/ 
	http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html, or other mirrors.
  SuSE		kernel-source-2.6.15-23-386		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.15-23-386 or kernel-smp-devel-2.6.15-23-386 on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.15-23-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

 A /dev/modem symbolic link is not set.

The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
-------------------------------------
 Resident PPP support modules are properly uncompressed .
----active COMM services are ------------
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:DD:C4:39  
This COMM mode should be closed before using the modem, or DNS services may fail.
Be sure to read the section about ppp related modules and aliases in Modem/YourSystem.txt
 ---- dmesg queries -------
[4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[4294671.138000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294671.139000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294671.139000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294671.243000] audit: initializing netlink socket (disabled)
[4294702.044000] ibm_acpi: ec object not found
[4294702.071000] pcc_acpi: loading...
[4294708.854000] apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac)
[4294708.854000] apm: overridden by ACPI.

  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the http://www.smlink.com  slmodem software.
  Check pppd version with:
    pppd --version
  See  http://linmodems.technion.ac.il/archive-fourth/msg03167.html
    
  debian_version is not yet providing pre-compiled drivers for WinModems


```

---

### Post by Fittersman on 2006-07-16
](*,)

---

