---
title: "Dell PowerEdge 1400 - Installing Ubuntu Server 10.04.4 LTS (Lucid Lynx)"
date: 2013-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by beatgr on 2013-06-12
Installation of Ubuntu Server 10.04.4 LTS (Lucid Lynx)
*Finally time to update my earlier 2009 (stable) Ubuntu Server 8.10 installation.*
[http://ubuntuforums.org/archive/index.php/t-1063456.html](http://ubuntuforums.org/archive/index.php/t-1063456.html)

I upgraded this PowerEdge 1400 Server with Dual 1000 MHz P III (Coppermine) processors,
this is the fastest processor this earlier motherboard will support (no Tualatin support).

In addition, Quieter Fans (FRONT FAN: 8C152, REAR FAN: 7C219 ) were installed (minimum 2,000 RPM) required by 
the Baseboard Management Controller (BMC) on the PowerEdge 1400 motherboard.
[http://en.wikipedia.org/wiki/Baseboard_management_controller#Baseboard_management_controller](http://en.wikipedia.org/wiki/Baseboard_management_controller#Baseboard_management_controller)

> Dell PowerEdge 1400
(earlier motherboard, no Pentium III Tualatin support)
Two 1000 MHz, 133 MHz processors, Processor Bus: 133 MHz, 256K L2 cache
2,024 Mb memory

Adaptec AIC-7899 Ultra 160/m SCSI Build 25309(on motherboard)
Channel 0: 4 SCSI hard drives -- NO RAID
Channel 1: Dell PV-100T DDS4 (Tape Drive)
Tape drive: Archive Python 06408-XXX
There is NO firmware update for the motherboard based AIC-7899

Network - Ethernet (2 ports)
Intel Pro/100 (on motherboard)
Intel Pro/100+ Add-on PCI Ethernet Adapter (PILA8470B)

Integrated Hardware Monitoring; 
Dell Remote Assistant Card Version 2.0 (DRAC II), latest firmware===
I will assume that you have the latest BIOS for this Dell PowerEdge 1400 installed.  "A09" was the last update from Dell.
*You DELL Boot screen will display the BIOS version.*
[http://www.dell.com/support/drivers/us/en/04/DriverDetails?driverId=R47691](http://www.dell.com/support/drivers/us/en/04/DriverDetails?driverId=R47691)

Boot Options
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

1) Configure the boot order so that Drive #1 (PowerEdge) is the first hard drive to boot. This will be the target drive for the Ubuntu installation.
2) Install Ubuntu Server 10.04.4 LTS (Lucid Lynx) from the LiveCD (or release) -- per instructions. 
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
3) I selected the Guided installation for the hard drive partitioning (Selection 4, Entire disk, setup LVM).
4) Ubuntu will detect the two Ethernet ports: eth0, eth1. I selected eth0 (motherboard port) as the Primary.
5) Your server should be connected to your home network router (DHCP server).  IF you configure your router earlier, 
you can map the Server's Name to a fixed IP address assignment.
4) When Ubuntu "comes up" the first time, you will get the BUSYBOX - the built-in shell. 

Type: **exit**, the server will complete the boot process and provide you with a command prompt, such as: username@server:"$

The problem is with default GRUB2 configuration with Ubuntu Server 10.04.4 on the PowerEdge 1400(SC).
==
GRUB2
*GRUB 2 is the default boot loader and manager for Ubuntu since version 9.10 (Karmic Koala).*
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

The user can create a custom file in which the user can place his own menu entries. This file will not be overwritten. By default, a custom file named 40_custom is available for use in the /etc/grub.d folder.

The primary configuration file for changing menu display settings is called grub and by default is located in the /etc/default folder.

There are multiple files for configuring the menu - /etc/default/grub mentioned above, 
and all the files in the /etc/grub.d/ directory.
==
THE FIX

"rootdelay=60" needs to be inserted in the default configuration of /etc/default/grub -- that look similar to this:
*This value "60" will vary depending upon your server / disk configuration.  Some have reported they needing delay values as high as 150.*
> GRUB_CMDLINE_LINUX_DEFAULT="quiet"

The modified line will look like this:
> GRUB_CMDLINE_LINUX_DEFAULT="rootdelay=60 quiet"
==
*Editing the /etc/default/grub file*
The first command line creates a back-up copy of the file. 
After the last character " ' " ... I had to type an additional space (spacebar) for the command to properly execute.
The second command line uses your text editor (nano, mousepad, gkedit, emacs, vi) to modify the lines in /etc/default/grub as shown above.
> sudo cp /etc/default/grub /etc/default/grub.'date +~%b-%d-%Y~%T'
sudo nano /etc/default/grub
*Save the file after the changes and close your editor.*

Now update the grub!
> sudo update-grub

Before rebooting the system, you should get the security / release updates for 10.04.4 LTS and apply them. 
sudo apt-get update

To upgrade to a newer release, from a terminal prompt enter:
> do-release-upgrade

*I synchronize the system clock with an NTP (Network Time Protocol) server over the Internet.*
> sudo aptitude install ntp ntpdate

Ubuntu 10.04.4 Server Guide
[https://help.ubuntu.com/10.04/serverguide/serverguide.pdf](https://help.ubuntu.com/10.04/serverguide/serverguide.pdf)

===
Good luck!
*from the trailing edge .....*

---

### Post by beatgr on 2013-06-12
Speaking of FANS, this is a design shortcoming with the 1400 model (minimum speed, rpm, required).
Some have started to Hack the BMC, since Dell has ignored -- and no BIOS adjustment selection.
[http://projects.nuschkys.net/page/2/](http://projects.nuschkys.net/page/2/)

Dell PowerEdge 2800 : Fan speed adjustment
[http://projects.nuschkys.net/2011/11/15/how-to-adjust-the-fan-thresholds-of-a-dell-poweredge/](http://projects.nuschkys.net/2011/11/15/how-to-adjust-the-fan-thresholds-of-a-dell-poweredge/)

This PowerEdge 1400 has the optional DRAC II card, a rebadged AMI MegaRAC 767.
The DRAC II is not based on IPMI, but shares similar concepts in function.
[http://lists.us.dell.com/pipermail/linux-poweredge/2004-October/016916.html](http://lists.us.dell.com/pipermail/linux-poweredge/2004-October/016916.html)
It can be addressed (connect) via a Java based web interface (Internet Explorer) so that you may view console, BMC error logs, etc. 
It can send out SNMP traps via the Ethernet port. 
Users can configure this using the *racadm* utility (Windows and RedHat) to configure settings.
[http://www.shikadi.net/hwwiki/Dell_DRAC_II](http://www.shikadi.net/hwwiki/Dell_DRAC_II)

Dell OpenManage[SUP]TM[/SUP] Remote Access Card II (DRAC II) User's Guide, courtesy of University of Waterloo (Canada)
[https://cs.uwaterloo.ca/~brecht/servers/docs/PowerEdge-2600/en/Drac/dra24bk1.pdf](https://cs.uwaterloo.ca/~brecht/servers/docs/PowerEdge-2600/en/Drac/dra24bk1.pdf)

*DRAC II occupies a single, full-length PCI slot. In addition to the processor, the card includes 16 MB of memory, flash RAM/nonvolatile random access memory (NV-RAM), onboard NIC for 10 Mbps Ethernet, PC Card interface, PCI controller, battery, real-time clock, and ESM2 connector.*

The Dell[SUP]TM[/SUP] Remote Assistant Card II (DRAC II) and Dell Remote Access Card III (DRAC III) provide users with the necessary tools and functionality to monitor, troubleshoot, and repair servers that are around the corner or around the world. 
[http://www.dell.com/content/topics/global.aspx/power/en/ps2q02_bell?c=us&l=en](http://www.dell.com/content/topics/global.aspx/power/en/ps2q02_bell?c=us&l=en)

The DRAC II card, by default, listens to DHCP (using bogus MAC addresses) for their PPP addresses (for dial-in users),
however the card's primary IP appears to be static-only. The default IP address is 10.0.0.1.

The cards only listen on two ports - TCP 5001 and 5123. 
Port 5123 show debugging messages, while port 5001 is used for the proprietary remote-access connections.

DRAC II v2.5 firmware from Dell can be extracted to a floppy disk for restting or performing a utility flash to the DRAC II.

I have not seen specific programs (racconf, racadm, ipmitool) referenced for usage with this earlier DRAC II option, under Ubuntu 10.04.4 LTS (Lucid Lynx).

---

### Post by beatgr on 2013-06-14
Answer to an earlier query about:

**Dell PowerEdge 1400 User's Guide**
[ftp://ftp.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_poweredge/poweredge-1400sc_User%27s%20Guide_en-us.pdf](ftp://ftp.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_poweredge/poweredge-1400sc_User%27s%20Guide_en-us.pdf)

**Dell PowerEdge 1400 System Management ISO Files**

Installation and System Management (ISM) v 4.5 
*Last version to support the Dell PowerEdge 1400/1400SC*
 ===
[http://ftp.us.dell.com/sysman/4.5_DOC_A00.ISO](http://ftp.us.dell.com/sysman/4.5_DOC_A00.ISO)
[http://ftp.us.dell.com/sysman/4.5_ISM_A00.ISO](http://ftp.us.dell.com/sysman/4.5_ISM_A00.ISO)
[http://ftp.us.dell.com/sysman/4.5_OM_SUU_A00.iso](http://ftp.us.dell.com/sysman/4.5_OM_SUU_A00.iso)
[http://ftp.us.dell.com/sysman/4.5_SDU_A00.ISO](http://ftp.us.dell.com/sysman/4.5_SDU_A00.ISO)
[http://ftp.us.dell.com/sysman/4.5_SMC_A00.ISO](http://ftp.us.dell.com/sysman/4.5_SMC_A00.ISO)
[http://ftp.us.dell.com/sysman/4.5_SUU_A00.iso](http://ftp.us.dell.com/sysman/4.5_SUU_A00.iso)

[http://support.dell.com/support/edoc...radmin/2.2/en/](http://support.dell.com/support/edoc...radmin/2.2/en/)

Administrator 2.2 is supported on the:
*Installation and Server Management CD version 4.5*

[http://support.dell.com/support/edoc...dme/readme.txt](http://support.dell.com/support/edoc...dme/readme.txt)
Server Administrator 2.2 is supported on the "Installation and Server Management" CD version 4.5. 

The following Dell PowerEdge systems are supported for "Installation and Server Management" CD version 4.5: 
 350, 500SC, 600SC, 650, 700, 750, 800, 830, 850, 1400, 1400SC, 1500SC, 1550, 1600SC, 1650, 1655MC, 
 1750, 1800, 1850, 1855, 2400, 2450, 2500, 2550, 2600, 2650, 2800, 2850, 4400, 4600, 6400, 6450, 6600, 6650, 6800, 6850, and 8450.

 The following Dell PowerVault(TM) systems are supported:
 PV 745N, 770N, and 775N.

 ================================================== ==============
 SUPPORTED OPERATING SYSTEMS
 ================================================== ==============

 * Microsoft(R) Windows(R) 2000 Server family (32-bit extension) 
 (includes Windows 2000 Server SP3 and greater, Windows 2000 
 Advanced Server SP3 and greater, and Windows 2000 Small Business Server [SBS], and Windows 2000 SBS SP1)

 * Microsoft Windows Server(TM) 2003 family (32-bit and 64-bit 
 extensions) (includes SP1 with Web, Standard, and Enterprise and x64 editions) and Microsoft Windows Server 2003 SBS

 * Red Hat(R) Enterprise Linux (AS, WS and ES), (version 3 and 4) 
 for Intel(R) x86 and Intel Extended Memory 64 Technology (EM64T) 

 * Novell(R) NetWare(R), version 6.5 (SP2 or later)

 * VMWare 2.5.1 ESX service console

---

