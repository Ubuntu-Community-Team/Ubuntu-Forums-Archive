---
title: "Dell PowerEdge 1400 Install"
date: 2009-02-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by beatgr on 2009-02-07
Installation of Ubuntu Server 8.10
> 
Dell PowerEdge 1400
(earlier motherboard, no Pentium III Tualatin support)
800 MHz, 133 MHz procesor with 256K L2 cache
2,024 Mb memory

Adaptec AIC-7899 Ultra 160/m SCSI Build 25309(on motherboard)
Channel 0: 4 SCSI hard drives -- NO RAID
Channel 1: Dell PV-100T DDS4 (Tape Drive)
*Tape drive: Archive Python 06408-XXX*
*There is NO firmware update for the motherboard based AIC-7899*

Network - Ethernet (2 ports)
Intel Pro/100 (on motherboard)
Intel Pro/100+ Add-on PCI Ethernet Adapter (PILA8470B)

Integrated Hardware Monitoring; Optional Dell Remote Assistant Card Version 2.0

Thanks to earlier posts, suggestions and answers from:
rjromero10;  movingover; Albinootje

1) This retired server previously ran Windows NT 4.0
2) Download from Dell website ANY BIOS updates for your PowerEdge computer.
A09 is the latest BIOS version for the PE 1400.
Format a blank floppy and copy the BIOS/boot image from the Dell download.
3) Reboot PowerEdge, booting server from the floppy drive.  Run the BIOS update, per Dell instructions.

4) At this point, I installed a copy of Windows 2000 Server SP4, on drive #2 of the 4 drives installed.  *I changed the boot order, so that Drive #2 was first hard drive to boot during this process.* After completing hardware driver and security updates (Microsoft Update), I am ready to install Ubuntu.

5) Configure the boot order so that Drive #1 (PowerEdge) is the first hard drive to boot.  This will be the target drive for the Ubuntu installation.
6) Install Ubuntu Server 8.10 from the LiveCD -- per instructions.  I selected the *Guided installation* for the hard drive partitioning (Selection 2, as I remember).
7) When the Ubuntu install tries to "come up" the first time, you will get the **busybox** - the built-in shell.  

Type *exit*, the server will complete the boot process and provide you with a command prompt, such as: username@server:"$

The problem is with this file:  /boot/grub/menu.lst

THE FIX

"rootdelay=60" needs to be inserted in the menu selection lines of /boot/grub/menu.lst -- 
that look similar to this:
>  
/boot/vmlinuz-2.6.27-7-server root=UUID=492ac531-c353-xxxx-xxxx-xxxxxxxxd913 ro quiet splash
I had 2 such lines in my file, (Ubuntu and Ubuntu recovery mode)

The modified line will look like this:
> 
/boot/vmlinuz-2.6.27-7-server root=UUID=492ac531-c353-xxxx-xxxx-xxxxxxxxd913 ro rootdelay=60 quiet splash

The first command line crates a back-up copy of the file.  
After the last character "`" ... I had to type an additional space (spacebar) for the command to properly execute.
The second command line uses your text editor (nano, mousepad, gkedit, emacs, vi) to modify the lines in menu.lst as shown above.
> 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.`date +~%b-%d-%Y~%T`
sudo nano /boot/grub/menu.lst
Save the file and close your editor.

Now update the grub!
> 
sudo update-grub

Before rebooting the system, you can run update. 
> sudo apt-get update

NOTE: I still have the ACPI notice during the boot process.
This appears to be a COMMON issue with Linux and many computers.
The Dell PE 1400 BIOS has NO ability (F2 - Setup) to adjust ACPI in BIOS
> 
[0.616031] .. MP-BIOS BUG: 8254 Timer not connected to IO-APIC


BTW, if you desire the GUI interface for the 8.10 Server, 
rather than the command line interface .. you can run:
> 
sudo apt-get install ubuntu-desktop
The desktop install took almost 20 minutes for my system.

Good luck!

---

### Post by beatgr on 2009-02-08
As a follow-up, some additional notes for the Ubuntu 8.10 Server installation.

These 3 errors appeared on monitor (ACPI and CDROM issues)
> 
[ 0.616031] .. MP-BIOS BUG: 8254 Timer not connected to IO-APIC
[xx.xxxxxx] .. end_request: I/O error, dev sr0, sector 1305216
[xx.xxxxxx] .. Buffer I/O error on dev sr0, logical block 163152


The Ubuntu installer configured the server for DHCP and used the Ethernet **eth1** port on the add-in Intel Ethernet card.
The Ethernet **eth0** motherboard port did not appear to load properly during initial CD install.
===
Ethernet **eth0** issue was addressed by configuring a Static IP address for Ubuntu server.
Edit */etc/network/interfaces* and enter IP address details 
(Example setup uses IP address 172.19.0.10):

sudo vi /etc/network/interfaces

Enter the following, save the file, then exit.
> 
# The primary network interface (eth0)
auto eth0
iface eth0 inet static
address 172.19.0.10
netmask 255.255.255.0
network 172.19.0.0
broadcast 172.19.0.255
gateway 172.19.0.1

Now you need to restart your network services using the following command

sudo /etc/init.d/networking restart

You need to setup manually DNS servers in the file *resolv.conf* 
when you are not using DHCP.

sudo vi /etc/resolv.conf

The config file will need to look like this:
> 
domain *yourISPdomain.com*
search *yourISPdomain.com*
nameserver *xxx.xxx.xxx.xxx*  (IP address of your ISP DNS server)

==
These Ubuntu 8.04 notes are useful for typical LAMP server setup.
[http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html)

beatgr

---

### Post by boleklolek on 2009-03-23
I have a powerEdge 4400 with the error in the scsi dirver i have to write exit in the busybos to get the system up and running. i dont know how to do a bios upgrade, i think i need windows :S and i dont have any copy or license, i there another way to apply the patch to the bios??


For the mp-bios error you may need put noapic in the kernel at boot time or in the kernel options in the grub menu.lst

thanks


pd i put a rootdelay=180 and it works, because the value of 60 dont works :S thanks to your post :D

---

### Post by javadewd on 2011-02-10
Not only was this great advice, but there were a few quirks I had to wrangle on my Dell PowerEdge 1400 (not 1400SC) --

1) You cannot put an ATI Radeon 9250 in the top slot. It treats it like an unknown SCSI card in the BIOS and taps your IRQs. I put it in the 4th slot under my SATA/RAID Controller

2) You *must* set the SCSI drive to be the 1st to boot if you are using the SCSI controller at all when you have a SATA Controller

3) The ServerWorks USB controller seems to be the only way to boot an IDE Optical Drive - the IDE controller on the SATA Controller would not boot or come up as bootable in the BIOS at all

With Ubuntu 10.10 - Desktop/Server/UEC loaded on this server I also have a Sound Blaster audio card, SATA/RAID controller, ATI Raedeon 9250 video card, two optical drives, a 500GB SATA RAID-1 array and a SCSI 36GB RAID-5 array installed as well as a decent Bluetooth USB dongle -- I hope to eventually get the 800MHz P-III's upgraded to 1GHz's soon. It's almost everything that I need to do what I need this server to do!

Now my two big problems are -- rhetorical questions, as I'm sure they are probably answered somewhere else in this forum : 

1) How do I back up the distro, so I can install another server with the exact same packages and such?

2) Where do I get the Dell disc(s) to enter the diagnostic partition to shut off the pesky "Previous Voltage Failure" message and keep it from saying "Strike F1 to Continue?"

Stay Classy, Ubuntu! :)

---

### Post by beatgr on 2012-02-09
Dell System Management ISO Files
Installation and System Management (ISM) v 4.5 was last to 
support Dell PowerEdge 1400/1400SC
===
[http://ftp.us.dell.com/sysman/4.5_DOC_A00.ISO](http://ftp.us.dell.com/sysman/4.5_DOC_A00.ISO)
[http://ftp.us.dell.com/sysman/4.5_ISM_A00.ISO](http://ftp.us.dell.com/sysman/4.5_ISM_A00.ISO)
[http://ftp.us.dell.com/sysman/4.5_OM_SUU_A00.iso](http://ftp.us.dell.com/sysman/4.5_OM_SUU_A00.iso)
[http://ftp.us.dell.com/sysman/4.5_SDU_A00.ISO](http://ftp.us.dell.com/sysman/4.5_SDU_A00.ISO)
[http://ftp.us.dell.com/sysman/4.5_SMC_A00.ISO](http://ftp.us.dell.com/sysman/4.5_SMC_A00.ISO)
[http://ftp.us.dell.com/sysman/4.5_SUU_A00.iso](http://ftp.us.dell.com/sysman/4.5_SUU_A00.iso)
 
[http://support.dell.com/support/edocs/software/svradmin/2.2/en/](http://support.dell.com/support/edocs/software/svradmin/2.2/en/)
 
Administrator 2.2 is supported on the "Installation and Server
Management" CD version 4.5
 
[http://support.dell.com/support/edocs/software/svradmin/2.2/en/Readme/readme.txt](http://support.dell.com/support/edocs/software/svradmin/2.2/en/Readme/readme.txt)
Server Administrator 2.2 is supported on the "Installation and Server Management" CD version 4.5. 

The following Dell PowerEdge systems are supported for 
"Installation and Server Management" CD version 4.5: 
350, 500SC, 600SC, 650, 700, 750, 800, 830, 850, 1400, 1400SC, 1500SC, 1550, 1600SC, 1650, 1655MC, 
1750, 1800, 1850, 1855, 2400, 2450, 2500, 2550, 2600, 2650, 2800, 2850, 4400, 4600, 6400, 6450, 6600, 6650, 6800, 6850, and 8450.
 
The following Dell PowerVault(TM) systems are supported:
PV 745N, 770N, and 775N.
 
================================================================
SUPPORTED OPERATING SYSTEMS
================================================================
 
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

