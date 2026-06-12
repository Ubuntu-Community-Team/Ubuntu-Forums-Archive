---
title: "Smartlink 1801 modem help!"
date: 2006-02-27
forum: Desktop Environments
---

### Post by eightbit on 2006-02-27
Could anyone help me with installing my modem?  I'd really like to log in using kubuntu instead of windows.   Actually thats the only reason why I still have a windows partition.  Anyways I'm running Kubuntu 5.10 and I have a smartlink 1801 mdoem.  Thanks in advance.  I tried sending modemdata.txt to linmodems.org but my mail was rejected.  Here's the modemdata.txt file:



 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-9-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2006_Feb_14
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-9-386
 USB modem not detected.


 The kernel was assembled with compiler:  3.4.5
 with current System compiler GCC=4.0.2

 Found make utility.

Checking for kernel-headers needed for compiling.
 Kernel-headers supporting compiling are resident: 

Modem candidates are at PCI_buses:  0000:01:08.0
    
Providing detail for device at  0000:01:08.0
  with vendor-ID:device-ID
	    ----:----
Class 0703: 10b9:545a   Modem: ALi Corporation SmartLink SmartPCI563 56K Modem (prog-if 00 [Generic])
  SubSystem 201f:545a  Unknown device 201f:545a
	Flags: bus master, medium devsel, latency 64, IRQ 11
 Checking for IRQ 11 sharing with modem.

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 10b9:545a 201f:545a ubuntu 2.6.12-9-386  3.4.5 4.0.2    i686

The SmartLink slamr driver supports this modem:
    10b9:545a  ALI545A SL1801
complemented by the SmartLink slmodemd.

 == Checking PCI IDs through modem chip suppliers ==

 Vendor 10b9 is Acer Labs, producing highly integrated motherboards and Ali components.
 The tight integration unfortunately ofter blocks identification of the modem chipset.
 Desired information may be gained by using a COMM console under MS Windows,
   and using ATI commands to elicit chipset and driver information.
 10b9:5450  ALI 5450 and  10b9:5451  ALI 5451 are controllers for unsupported "sound  modems"
 
 10b9:545a ALI545A SL1801 and 10b9:545a  ALI 5459 SmartPCI561 have SmartLink chipsets.


 SmartLink at [http://www.smlink.com/](http://www.smlink.com/) owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  [http://www.smlink.com/main/index1.php?ln=en&main_id=40](http://www.smlink.com/main/index1.php?ln=en&main_id=40)
 But a more recent code and a much broader license for other chipset support,
 can be downloaded from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)  
 Though not always needed, download the files: 
   slmodem-CurrentVersion.tar.gz - provides the most general code package.
   SLMODEMD.gcc3 - provides a compiled slmodemd 
   ungrab-winmodem.tar.gz  -  may be needed for usage with slamr. 
 Details on their usage are in Slmodem.txt, Slmodem-ALSA.txt and
 [http://linmodems.technion.ac.il/slmodem-serial.html](http://linmodems.technion.ac.il/slmodem-serial.html)


  ======= PCI_ID checking completed ====== 
 Update=2006_Feb_14
A PCMCIA CardBus is not detected on this System.
drwxr-xr-x  2 root root 0 2006-02-26 21:32 /dev/.udevdb

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


Checking the /etc/apt/sources.list
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling


    /usr/bin/gcc -> gcc-4.0
      
 The Major.Minor versions differ in the designated compiler 4.0.2 and the 3.4.5 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See [http://linmodems.technion.ac.il/archive-fifth/msg04252.html](http://linmodems.technion.ac.il/archive-fifth/msg04252.html) 
 
 A /dev/modem symbolic link is not set.

The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe_mppc
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/YourModem.txt
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294668.462000] CPU serial number disabled.
[4294669.738000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294669.750000] audit: initializing netlink socket (disabled)
[4294721.477000] ibm_acpi: ec object not found
[4294744.090000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294744.090000] apm: overridden by ACPI.
  ubuntu is not yet providing pre-compiled drivers for WinModems

---

### Post by towsonu2003 on 2006-03-02
check out the wiki link in my signature. smartlink will work with linux.

---

### Post by Matchless on 2006-03-03
Hi,
      I have just battled with a couple of Smartlink modems and finally got it to work here is a copy of my own howto. My Smartlink modems are internal LG modems and one chip on the board has a lable pasted on that you can remove or you can go into modem diagnostics in Windows and see the chip number. I hope this helps:
**_Addtional Smartlink internal modem howto:_**

I have found that in the latest Kubuntu Breezy update with Linux-headers 2.6.12-10-386 version 2.6.12-10-28 the Smartlink drivers in available in the Universe does not work.
All the steps in the wiki dialupmodemhow to, using the sl-modem-source file found on the universe repositories, compiles very successfully without any errors and the modem is detected nicely in KPPP and can be properly queried there as well. Then when connecting it runs and then fails to dial. The command ATDT also fails on a terminal and then locks the modem up, which can only be released by rebooting or using sudo ungrab-winmodem and sudo /etc/init.d/sl-modem-daemon restart. I have experienced this on various different PC's with Breezy and can recall that it did work with the first initial CD distribution of Breezy, but have not proven that again.

The problem can be overcome by using the  file slmodem-2.9.11-20051101.tar.gz that can be downloaded from the [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/) site. You can then use the sl-modem daemon that can be downloaded from the universe repositories and your modem will be working again. Assuming you have successfully compiled and installed the driver from the repositories, but the dialing does not work. If not, you have to install all the pre requisites up to that stage before continuing, gcc3.4, correct version linux headers etc (see dialupmodemhowto in wiki)
 _These steps can be followed:_
Use Synaptic to uninstall the sl-modem-modules, sl-modem-source and sl-modem-daemon files completely after determining that they do not work with your modem.
Now extract the file slmodem-2.9.11-20051101.tar.gz to the Desktop (use right click, extract here)
Rename this extracted folder to an easier name i.e. slmodem
CD in to this folder slmodem
sudo make
sudo make install
modprobe slamr
dmesg | grep slamr
  Check that no error messages were given during the last 2
Use Synaptic to install sl-modem-daemon from the repositories, or from your cache if still there
Use KPPP to test your modem, select /dev/modem and enter modem details and under Device do a Query Modem, if this works you are 99% there.
Now edit the /etc/default/sl-modem-daemon and change the line SLMODEMD_COUNTRY=SOUTHAFRICA                     (replace the USA default)
Do a reboot and check if your KPPP Modem Query shows South Africa
Now try and connect and the dialling should work

Note:  If the modem freezes due to interupting it or whatever you can save rebooting if you install ungrab-winmodem, also from the above site. You can then set up a Desktop icon, by right clicking with the following two commands sudo modprobe-ungrab-winmodem and sudo /etc/init.d/sl-modem-daemon restart and this icon can then just be clicked to properly reset your modem without rebooting.
Smartlink modems using Netodragon chip ND92XPA works well with this, but chip MDV92XP does not work in Breezy at all, but I recall using it in Hoary successfully. This again has not been proven again.

---

### Post by towsonu2003 on 2006-03-03
[QUOTE=Matchless]
I have found that in the latest Kubuntu Breezy update with Linux-headers 2.6.12-10-386 version 2.6.12-10-28 the Smartlink drivers in available in the Universe does not work.[/QUOTE]
Did you try the precompiled slmodemd (works only with alsa I believe???) from linmodems.org? Works nicely with mine (only in Ubuntu, which is weird).

---

### Post by Matchless on 2006-03-04
[QUOTE=towsonu2003]Did you try the precompiled slmodemd (works only with alsa I believe???) from linmodems.org? Works nicely with mine (only in Ubuntu, which is weird).[/QUOTE]

 Yes, I used it, but only whith the repository sl-modem source and not with the latest driver as shown above. I believe it has the ungrab-winmodem option includedand will give it a go soon.
Thanks

---

### Post by towsonu2003 on 2006-03-04
[QUOTE=Matchless]Yes, I used it, but only whith the repository sl-modem source and not with the latest driver as shown above.
[/QUOTE]
it may be different with your modem: I just downloaded it, copied to /usr/bin, chmod u+x, and run with 
```

sudo nice[1] -n -19 slmodemd -a -c USA modem:1
```
in every boot. I don't have anything related to sl-modem from the repos. There was no compiling, even no reading (well, after I spent 3 months trying to understand what to do :) ). The good thing with this is that it is *supposed*[2] to run with anything that can modprobe snd-atiixp-modem. 

[1]high cpu usage kills connection without nicing it to high priority
[2]does not work with any other distro :( in my computer

Again, usefulness of this may be different / unavailable with your modem. 
[QUOTE=Matchless]
 I believe it has the ungrab-winmodem option includedand will give it a go soon.[/quote]
that ungrab-modem thing kills my installations (mouse gets borked, all sorts of problems, and not useful at all in this specific computer. I'm not sure whether I'm whining or trying to help at this point though :PpPp

---

