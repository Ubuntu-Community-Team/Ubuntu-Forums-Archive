---
title: "Running a Windows Partition in VMWare Without Installing Windows Again"
date: 2007-03-12
forum: Desktop Environments
---

### Post by ravisghosh on 2007-03-12
I found this great piece of instructions regarding running physical windows partition in linux using vmware. Here is the link [http://oopsilon.com/Running-a-Windows-Partition-in-VMware]("http://oopsilon.com/Running-a-Windows-Partition-in-VMware"). Its really simple enough to understand for a noob like me. But I found something which I could not understand. The author mentioned "If you have Windows on one hard disk and Linux on another, use the Windows disk in the command below, otherwise just use the disk device containing the Windows partition" and in his example, he used "parted /dev/hda" which is reccommended if windows is on one disk and linux on another. But the results from "unit s" command  shows that he has windows and linux both on "hda" only. "Otherwise just use the disk device containing the Windows partition" means to me that if windows and linux is on same disk, then one should windows disk device, i.e., "hda1" and this is what he should have used in his example. This thing is confusing.

Here is what I got when I fired parted on /dev/sda and /dev/sda1 (windows disk)

[COLOR="Red"][root@bluehead shantanu]# parted /dev/sda
GNU Parted 1.8.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s 
(parted) print 
Model: ATA SAMSUNG SV4002H (scsi) 
Disk /dev/sda: 78242975s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number   Start               End                Size               Type           File system    Flags
1              63s                 10233404s    10233342s    primary       fat32              boot 
2              10233405s     78236549s    68003145s    extended                           lba 
5              10233468s     20225834s    9992367s      logical        fat32               lba 
6              20225898s     24434864s    4208967s      logical        linux-swap 
7              24434928s     37126214s    12691287s    logical        ext3 
8              37126278s     64774079s     27647802s    logical        ext3 
9               64774143s     78236549s    13462407s    logical        fat32 

_________________________


[root@bluehead shantanu]# parted /dev/sda1
GNU Parted 1.8.2
Using /dev/sda1
Welcome to GNU Parted! Type 'help' to view a list of commands. 
(parted) unit s 
(parted) print 
Model: Unknown (unknown)
Disk /dev/sda1: 10233341s
Sector size (logical/physical): 512B/512B 
Partition Table: loop

Number    Start     End                 Size                File system     Flags
1               0s         10233341s     10233342s     fat32[/COLOR]

So, we have 2 sets of values ( 10233341s and 78242975s, and other values), Could anyone please suggest which one to use. I just want to be sure not to damage my partition and ruin my box.

As you could see I have got 7 partitions out of which partition 1 is windows' C and partition 5 and 9 (fat32) are used for common data (music, etc) used by both linux and windows. Will it be possible to access these partitions simultaneously from native linux and virtual windows? Will that cause any damage? 

Another thing is that I use windows boot menu to go to grub and then boot linux so as to keep mbr unaffected. Will that affect virtual machine configuration in anyway. I have heard that booting into the same partition by 2 OS's will destroy the partition. Any thought on that.

---

### Post by jondecker76 on 2007-03-12
i'l have to try this out when I get home - i dual boot with Windows on another drive - thanks for the info

---

### Post by ravisghosh on 2007-03-27
I configured vmplayer using vmware-config.pl and chose recommended options.

[COLOR="Red"][root@bluehead shantanu]# /usr/bin/vmware-config.pl 
Making sure services for VMware Player are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] /usr/share/icons

The file 
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-snapshot.png that
this program was about to install already exists.  Overwrite? [yes] y

The file 
/usr/share/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-vmware-snapshot.png
that this program was about to install already exists.  Overwrite? [yes] y

The file /usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-team.png
that this program was about to install already exists.  Overwrite? [yes] y

The file 
/usr/share/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-vmware-team.png
that this program was about to install already exists.  Overwrite? [yes] y

The file /usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-vm.png 
that this program was about to install already exists.  Overwrite? [yes] y

The file 
/usr/share/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-vmware-vm.png
that this program was about to install already exists.  Overwrite? [yes] y

The file 
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-vmdisk.png that 
this program was about to install already exists.  Overwrite? [yes] y

The file 
/usr/share/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-vmware-vmdisk.png
that this program was about to install already exists.  Overwrite? [yes] y

The file 
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-vmfoundry.png 
that this program was about to install already exists.  Overwrite? [yes] y

The file 
/usr/share/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-vmware-vmfoundry.png
that this program was about to install already exists.  Overwrite? [yes] y

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] /usr/share/applications

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] /usr/share/pixmaps

This program previously created the file /dev/parport1, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport2, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport3, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet0, and was about to remove 
it.  Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] no

Do you want networking for your virtual machines? (yes/no/help) [yes] y

This program previously created the file /dev/vmnet1, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet2, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet3, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet4, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet5, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet6, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet7, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet8, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet9, and was about to remove 
it.  Somebody else apparently did it already.

Would you prefer to modify your existing networking configuration using the 
wizard or the editor? (wizard/editor/help) [wizard] wizard

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] yes

Configuring a NAT network for vmnet8.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] yes

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.177.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes] y

This system appears to have a DHCP server configured for normal use.  Beware 
that you should teach it how not to interfere with VMware Player's DHCP server.
There are two ways to do this:

1) Modify the file /etc/dhcpd.conf to add something like:

subnet 192.168.177.0 netmask 255.255.255.0 {
# Note: No range is given, vmnet-dhcpd will deal with this subnet.
}

2) Start your DHCP server with an explicit list of network interfaces to deal 
with (leaving out vmnet8). e.g.:

dhcpd eth0

Consult the dhcpd(8) and dhcpd.conf(5) manual pages for details.

Hit enter to continue. 

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 192.168.177.0.

Do you wish to configure another NAT network? (yes/no) [no] n

Do you want to be able to use host-only networking in your virtual machines? 
[yes] y

Configuring a host-only network for vmnet1.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] y

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.13.0/255.255.255.0 appears to be unused.

This system appears to have a DHCP server configured for normal use.  Beware 
that you should teach it how not to interfere with VMware Player's DHCP server.
There are two ways to do this:

1) Modify the file /etc/dhcpd.conf to add something like:

subnet 172.16.13.0 netmask 255.255.255.0 {
# Note: No range is given, vmnet-dhcpd will deal with this subnet.
}

2) Start your DHCP server with an explicit list of network interfaces to deal 
with (leaving out vmnet1). e.g.:

dhcpd eth0

Consult the dhcpd(8) and dhcpd.conf(5) manual pages for details.

Hit enter to continue. 

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 172.16.13.0.

Do you wish to configure another host-only network? (yes/no) [no] n

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Player 1.0.3 build-34682 for Linux for this running
kernel completed successfully.

You can now run VMware Player by invoking the following command: 
"/usr/bin/vmplayer".

Enjoy,

--the VMware team

[root@bluehead shantanu]#[/COLOR]

If I start vmplayer as normal user (the user is added in "disk" group), it gives this error:

[COLOR="Red"]
[shantanu@bluehead ~]$ vmplayer
/usr/lib/vmware/bin/vmplayer: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)[/COLOR]

Running vmplayer as root, it does give the above error but also opens the "open virtual machine" diaglog and lets me select WindowsXP.vmx. But now when I start windows (by selecting OS and then vmware profile), it ends in the infamous "blue screen of death" and vmplayer restarts again showing me the option to select which OS to boot and again the "blue screen of death."

Here is my vmware log file:

[COLOR="Red"]
Mar 26 04:54:53: vmx| Log for VMware Player pid=4915 version=1.0.3 build=build-34682 option=Release
Mar 26 04:54:53: vmx| Command line: "/usr/lib/vmware/bin/vmware-vmx" "-@" "pipe=/tmp/vmware-root/vmx3c042d23f8a2a0f9;vm=3c042d23f8a2a0f9" "/home/shantanu/vmware-windows/WindowsXP.vmx"
Mar 26 04:54:53: vmx| UI Connecting to pipe '/tmp/vmware-root/vmx3c042d23f8a2a0f9' with user '(null)'
Mar 26 04:54:53: vmx| Using system libcrypto, version 90703F
Mar 26 04:54:53: vmx| pcpu #0 CPUID numEntries=2 GenuntelineI
Mar 26 04:54:53: vmx| pcpu #0 CPUID version=0x686 id1.edx=0x383f9ff id1.ecx=0x0 id1.ebx=0x2
Mar 26 04:54:53: vmx| pcpu #0 CPUID id80.eax=3020101 id81.edx=0xc040882 id81.ecx=0x0
Mar 26 04:54:53: vmx| CPUID id1.edx: 0x383f9ff id1.ecx: 0 id81.edx: 0xc040882 id81.ecx: 0
Mar 26 04:54:53: vmx| CPUID id88.ecx: 0 id88.edx: 0xc040882
Mar 26 04:54:53: vmx| Setup symlink /var/run/vmware/%2fhome%2fshantanu%2fvmware%2dwindows%2fWindowsXP%2evmx -> /var/run/vmware/root/4915
Mar 26 04:54:53: vmx| ACL_InitCapabilities: here 1 (bug 63252)
Mar 26 04:54:53: vmx| changing directory to /home/shantanu/vmware-windows/.
Mar 26 04:54:53: vmx| Config file: /home/shantanu/vmware-windows/WindowsXP.vmx
Mar 26 04:54:53: vmx| Unable to find WindowsXP.vmss.  Setting vmState to NULL.
Mar 26 04:54:53: vmx| Unable to find WindowsXP.vmss.  Setting vmState to NULL.
Mar 26 04:54:53: vmx| DISKLIB-DEVCRL: Facts for /dev/sda: Cap=78242976 Phys C/H/S=4870/255/63 BIOS C/H/S=4870/255/63 Adap=SCSI
Mar 26 04:54:53: vmx| LOG failed to remove /home/shantanu/vmware-windows/vmware-2.log failed: No such file or directory
Mar 26 04:54:53: vmx| VMXVmdbCbVmVmxExecState: Exec state change requested to state poweredOn without reset
Mar 26 04:54:53: vmx| TOOLS delaying state change request to state 3
Mar 26 04:54:53: vmx| PowerOn
Mar 26 04:54:53: vmx| Host ACPI: can't find SRAT
Mar 26 04:54:53: vmx| Unable to find WindowsXP.vmss.  Setting vmState to NULL.
Mar 26 04:54:53: vmx| Unable to find WindowsXP.vmss.  Setting vmState to NULL.
Mar 26 04:54:53: vmx| HOST sysname Linux, nodename bluehead, release 2.6.20-ck, version #1 SMP PREEMPT Thu Mar 1 01:15:49 GMT 2007, machine i686, SMP, hz=1000
Mar 26 04:54:53: vmx| DICT --- USER PREFERENCES
Mar 26 04:54:53: vmx| DICT       pref.grabOnKeyPress = FALSE
Mar 26 04:54:53: vmx| DICT       pref.eula.0.appName = VMware Player
Mar 26 04:54:53: vmx| DICT   pref.eula.0.buildNumber = 34682
Mar 26 04:54:53: vmx| DICT            pref.eula.size = 1
Mar 26 04:54:53: vmx| DICT    pref.autoFitFullScreen = fitHostToGuest
Mar 26 04:54:53: vmx| DICT     pref.view.navBar.type = favorites
Mar 26 04:54:53: vmx| DICT     pref.mruDest0.present = FALSE
Mar 26 04:54:53: vmx| DICT  pref.mruDest0.destString = 
Mar 26 04:54:53: vmx| DICT        pref.mruDest0.user = 
Mar 26 04:54:53: vmx| DICT     pref.mruDest1.present = FALSE
Mar 26 04:54:53: vmx| DICT  pref.mruDest1.destString = 
Mar 26 04:54:53: vmx| DICT        pref.mruDest1.user = 
Mar 26 04:54:53: vmx| DICT     pref.mruDest2.present = FALSE
Mar 26 04:54:53: vmx| DICT  pref.mruDest2.destString = 
Mar 26 04:54:53: vmx| DICT        pref.mruDest2.user = 
Mar 26 04:54:53: vmx| DICT     pref.mruDest3.present = FALSE
Mar 26 04:54:53: vmx| DICT  pref.mruDest3.destString = 
Mar 26 04:54:53: vmx| DICT        pref.mruDest3.user = 
Mar 26 04:54:53: vmx| DICT     pref.mruDest4.present = FALSE
Mar 26 04:54:53: vmx| DICT  pref.mruDest4.destString = 
Mar 26 04:54:53: vmx| DICT        pref.mruDest4.user = 
Mar 26 04:54:53: vmx| DICT     pref.mruDest5.present = FALSE
Mar 26 04:54:53: vmx| DICT  pref.mruDest5.destString = 
Mar 26 04:54:53: vmx| DICT        pref.mruDest5.user = 
Mar 26 04:54:53: vmx| DICT     pref.mruDest6.present = FALSE
Mar 26 04:54:53: vmx| DICT  pref.mruDest6.destString = 
Mar 26 04:54:53: vmx| DICT        pref.mruDest6.user = 
Mar 26 04:54:53: vmx| DICT     pref.mruDest7.present = FALSE
Mar 26 04:54:53: vmx| DICT  pref.mruDest7.destString = 
Mar 26 04:54:53: vmx| DICT        pref.mruDest7.user = 
Mar 26 04:54:53: vmx| DICT       webUpdate.checkLast = 1174444035
Mar 26 04:54:53: vmx| DICT pref.vmplayer.vmPos0.index = 2
Mar 26 04:54:53: vmx| DICT pref.vmplayer.vmPos0.vmPath = /vm/#1ed2b964990191e9/
Mar 26 04:54:53: vmx| DICT pref.vmplayer.vmPos0.geometry = 648x537+0+0
Mar 26 04:54:53: vmx| DICT pref.vmplayer.vmPos1.index = 1
Mar 26 04:54:53: vmx| DICT pref.vmplayer.vmPos1.vmPath = /vm/#db84dc1cd92b0266/
Mar 26 04:54:53: vmx| DICT pref.vmplayer.vmPos1.geometry = 728x457+284+172
Mar 26 04:54:53: vmx| DICT pref.vmplayer.vmPos2.index = 0
Mar 26 04:54:53: vmx| DICT pref.vmplayer.vmPos2.vmPath = /vm/#3c042d23f8a2a0f9/
Mar 26 04:54:53: vmx| DICT pref.vmplayer.vmPos2.geometry = 728x457+284+0
Mar 26 04:54:53: vmx| DICT --- USER DEFAULTS
Mar 26 04:54:53: vmx| DICT --- HOST DEFAULTS
Mar 26 04:54:53: vmx| DICT        vmplayer.searchbar = FALSE
Mar 26 04:54:53: vmx| DICT    vmnet1.hostonlyaddress = 172.16.41.1
Mar 26 04:54:53: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Mar 26 04:54:53: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Mar 26 04:54:53: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Mar 26 04:54:53: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Mar 26 04:54:53: vmx| DICT                    libdir = /usr/lib/vmware
Mar 26 04:54:53: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Mar 26 04:54:53: vmx| DICT --- SITE DEFAULTS
Mar 26 04:54:53: vmx| DICT                  tag.help = introduction.htm
Mar 26 04:54:53: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Mar 26 04:54:53: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Mar 26 04:54:53: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Mar 26 04:54:53: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Mar 26 04:54:53: vmx| DICT             tag.netConfig = devices_netadapter.htm
Mar 26 04:54:53: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Mar 26 04:54:53: vmx| DICT          tag.serialConfig = devices_serial.htm
Mar 26 04:54:53: vmx| DICT           tag.soundConfig = devices_sound.htm
Mar 26 04:54:53: vmx| DICT             tag.memConfig = configvm_memory.htm
Mar 26 04:54:53: vmx| DICT            tag.miscConfig = configvm.htm
Mar 26 04:54:53: vmx| DICT             tag.usbConfig = devices_usb.htm
Mar 26 04:54:53: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Mar 26 04:54:53: vmx| DICT                 tag.tools = vmtools.htm
Mar 26 04:54:53: vmx| DICT --- COMMAND LINE
Mar 26 04:54:53: vmx| DICT             gui.available = TRUE
Mar 26 04:54:53: vmx| DICT --- CONFIGURATION
Mar 26 04:54:53: vmx| DICT            config.version = 8
Mar 26 04:54:53: vmx| DICT         virtualHW.version = 4
Mar 26 04:54:53: vmx| DICT             uuid.location = 56 4d 89 a1 9f 06 e7 38-a6 7f b2 e5 8a 3b 79 36
Mar 26 04:54:53: vmx| DICT                 uuid.bios = 56 4d 89 a1 9f 06 e7 38-a6 7f b2 e5 8a 3b 79 36
Mar 26 04:54:53: vmx| DICT               uuid.action = create
Mar 26 04:54:53: vmx| DICT        checkpoint.vmState = WindowsXP.vmss
Mar 26 04:54:53: vmx| DICT               displayName = Windows XP Professional
Mar 26 04:54:53: vmx| DICT                annotation = 
Mar 26 04:54:53: vmx| DICT guestinfo.vmware.product.long = 
Mar 26 04:54:53: vmx| DICT guestinfo.vmware.product.url = 
Mar 26 04:54:53: vmx| DICT                   guestOS = winxppro
Mar 26 04:54:53: vmx| DICT                  numvcpus = 1
Mar 26 04:54:53: vmx| DICT                   memsize = 128
Mar 26 04:54:53: vmx| DICT                     paevm = FALSE
Mar 26 04:54:53: vmx| DICT   sched.mem.pshare.enable = TRUE
Mar 26 04:54:53: vmx| DICT     MemAllowAutoScaleDown = FALSE
Mar 26 04:54:53: vmx| DICT               MemTrimRate = -1
Mar 26 04:54:53: vmx| DICT                     nvram = WindowsXP.nvram
Mar 26 04:54:53: vmx| DICT              mks.enable3d = FALSE
Mar 26 04:54:53: vmx| DICT           vmmouse.present = FALSE
Mar 26 04:54:53: vmx| DICT          vmmouse.fileName = auto detect
Mar 26 04:54:53: vmx| DICT            tools.syncTime = TRUE
Mar 26 04:54:53: vmx| DICT       tools.remindinstall = FALSE
Mar 26 04:54:53: vmx| DICT isolation.tools.hgfs.disable = FALSE
Mar 26 04:54:53: vmx| DICT isolation.tools.dnd.disable = FALSE
Mar 26 04:54:53: vmx| DICT isolation.tools.copy.enable = TRUE
Mar 26 04:54:53: vmx| DICT isolation.tools.paste.enabled = TRUE
Mar 26 04:54:53: vmx| DICT            gui.restricted = FALSE
Mar 26 04:54:53: vmx| DICT         ethernet0.present = TRUE
Mar 26 04:54:53: vmx| DICT  ethernet0.connectionType = nat
Mar 26 04:54:53: vmx| DICT     ethernet0.addressType = generated
Mar 26 04:54:53: vmx| DICT ethernet0.generatedAddress = 00:0c:29:3b:79:36
Mar 26 04:54:53: vmx| DICT ethernet0.generatedAddressOffset = 0
Mar 26 04:54:53: vmx| DICT               usb.present = TRUE
Mar 26 04:54:53: vmx| DICT   usb.generic.autoconnect = TRUE
Mar 26 04:54:53: vmx| DICT             sound.present = TRUE
Mar 26 04:54:53: vmx| DICT          sound.virtualdev = sb16
Mar 26 04:54:53: vmx| DICT            ide0:0.present = TRUE
Mar 26 04:54:53: vmx| DICT           ide0:0.fileName = WindowsXP.vmdk
Mar 26 04:54:53: vmx| DICT               ide0:0.mode = independent-persistent
Mar 26 04:54:53: vmx| DICT         ide0:0.deviceType = rawDisk
Mar 26 04:54:53: vmx| DICT               ide0:0.redo = 
Mar 26 04:54:53: vmx| DICT       ide0:0.writeThrough = FALSE
Mar 26 04:54:53: vmx| DICT     ide0:0.startConnected = TRUE
Mar 26 04:54:53: vmx| DICT            ide1:0.present = TRUE
Mar 26 04:54:53: vmx| DICT           ide1:0.fileName = /dev/cdrom
Mar 26 04:54:53: vmx| DICT         ide1:0.deviceType = atapi-cdrom
Mar 26 04:54:53: vmx| DICT       ide1:0.writeThrough = FALSE
Mar 26 04:54:53: vmx| DICT     ide1:0.startConnected = TRUE
Mar 26 04:54:53: vmx| DICT           floppy0.present = TRUE
Mar 26 04:54:53: vmx| DICT          floppy0.fileName = /dev/fd0
Mar 26 04:54:53: vmx| DICT    floppy0.startConnected = TRUE
Mar 26 04:54:53: vmx| DICT           serial0.present = FALSE
Mar 26 04:54:53: vmx| DICT           serial1.present = FALSE
Mar 26 04:54:53: vmx| DICT         parallel0.present = FALSE
Mar 26 04:54:53: vmx| DICT --- USER DEFAULTS
Mar 26 04:54:53: vmx| DICT --- HOST DEFAULTS
Mar 26 04:54:53: vmx| DICT        vmplayer.searchbar = FALSE
Mar 26 04:54:53: vmx| DICT    vmnet1.hostonlyaddress = 172.16.41.1
Mar 26 04:54:53: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Mar 26 04:54:53: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Mar 26 04:54:53: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Mar 26 04:54:53: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Mar 26 04:54:53: vmx| DICT                    libdir = /usr/lib/vmware
Mar 26 04:54:53: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Mar 26 04:54:53: vmx| DICT --- SITE DEFAULTS
Mar 26 04:54:53: vmx| DICT                  tag.help = introduction.htm
Mar 26 04:54:53: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Mar 26 04:54:53: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Mar 26 04:54:53: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Mar 26 04:54:53: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Mar 26 04:54:53: vmx| DICT             tag.netConfig = devices_netadapter.htm
Mar 26 04:54:53: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Mar 26 04:54:53: vmx| DICT          tag.serialConfig = devices_serial.htm
Mar 26 04:54:53: vmx| DICT           tag.soundConfig = devices_sound.htm
Mar 26 04:54:53: vmx| DICT             tag.memConfig = configvm_memory.htm
Mar 26 04:54:53: vmx| DICT            tag.miscConfig = configvm.htm
Mar 26 04:54:53: vmx| DICT             tag.usbConfig = devices_usb.htm
Mar 26 04:54:53: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Mar 26 04:54:53: vmx| DICT                 tag.tools = vmtools.htm
Mar 26 04:54:53: vmx| DICT --- GLOBAL SETTINGS
Mar 26 04:54:53: vmx| Msg_Hint: msg.guestos.xp (shown)
Mar 26 04:54:53: vmx| WSSCAN: reserved mem (in MB) min=32 max=224 recommended=224
Mar 26 04:54:53: vmx|         hostMem=256 maxAllowedAll=4096 maxAllowedVM=3600
Mar 26 04:54:53: vmx|         totOverhead=16
Mar 26 04:54:53: vmx| WSSCAN: used rec mem (in MB) 224
Mar 26 04:54:53: vmx| WSSCAN: Overhead 39153 paged 5278 nonpaged 4096 maxFBSize
Mar 26 04:54:53: vmx| WSSCAN 1 1 57344 -1 57344 -1 50 0
Mar 26 04:54:53: vmx| LICENSE: Running in restricted mode
Mar 26 04:54:53: vmx| STATDECLGROUP stats Root "" null
Mar 26 04:54:53: vmx| Host CPUID features: version 0x688 id1.edx 0x383f9ff id1.ecx 0x0 id81.edx 0xc040882 id81.ecx 0x0
Mar 26 04:54:53: vmx| CPU.cpuFeatures = 0x735e02
Mar 26 04:54:53: vmx| CPUID after masking: version 0x688 id1.edx 0x383fbff id1.ecx 0x0 id81.edx 0xc040882 id81.ecx 0x0 id88.ecx 0x0
Mar 26 04:54:53: vmx| CPU.cpuFeatures = 0x8735e02
Mar 26 04:54:53: vmx| KHZEstimate 996822
Mar 26 04:54:53: vmx| MHZEstimate 997
Mar 26 04:54:53: vmx| NumVCPUs 1
Mar 26 04:54:53: vmx| UUID: location-UUID is 56 4d 89 a1 9f 06 e7 38-a6 7f b2 e5 8a 3b 79 36
Mar 26 04:54:53: vmx| MM: Using partialmap, 32768 pages AC 0 CE 1 TM 0 DOHU 0
Mar 26 04:54:53: vmx| UUID: canonical path is /home/shantanu/vmware-windows/WindowsXP.vmx
Mar 26 04:54:53: vmx| UUID: location-UUID is 56 4d 89 a1 9f 06 e7 38-a6 7f b2 e5 8a 3b 79 36
Mar 26 04:54:53: vmx| MM: using fileName /home/shantanu/vmware-windows/564d89a1-9f06-e738-a67f-b2e58a3b7936.vmem for paging
Mar 26 04:54:53: vmx| Msg_Reset:
Mar 26 04:54:53: vmx| ----------------------------------------
Mar 26 04:54:53: vmx| Opened paging file /home/shantanu/vmware-windows/564d89a1-9f06-e738-a67f-b2e58a3b7936.vmem
Mar 26 04:54:54: vmx| Mapped mainmem as pageable
Mar 26 04:54:54: vmx| MStat: Creating Stat vm.uptime
Mar 26 04:54:54: vmx| DISK: OPEN ide0:0 '/home/shantanu/vmware-windows/WindowsXP.vmdk' independent-persistent R[(null)]
Mar 26 04:54:54: vmx| AIOGNRC: Starting 4 I/O threads.
Mar 26 04:54:54: vmx| DISKLIB-DSCPTR: Opened [0]: "WindowsXP.mbr" 0 (0xa)
Mar 26 04:54:54: vmx| DISKLIB-DEVCRL: Facts for /dev/sda: Cap=78242976 Phys C/H/S=4870/255/63 BIOS C/H/S=4870/255/63 Adap=SCSI
Mar 26 04:54:54: vmx| DISKLIB-DSCPTR: Opened [1]: "/dev/sda" 63 (0xa)
Mar 26 04:54:54: vmx| DISKLIB-LINK  : Opened '/home/shantanu/vmware-windows/WindowsXP.vmdk' (0xa): fullDevice, 78242975 sectors / 38205 Mb.
Mar 26 04:54:54: vmx| DISKLIB-LIB   : Opened "/home/shantanu/vmware-windows/WindowsXP.vmdk" (flags 0xa).
Mar 26 04:54:54: vmx| DISK: OPEN '/home/shantanu/vmware-windows/WindowsXP.vmdk' Geo (4870/255/63) BIOS Geo (4870/255/63) freeSpace=10026Mb
Mar 26 04:54:54: vmx| TimeTracker host to guest rate conversion 10667194271712 @ 996822000Hz -> 10667194271712 @ 996822000Hz
Mar 26 04:54:54: vmx| TimeTracker host to guest rate conversion ((x * 2147483648) >> 31) + 0
Mar 26 04:54:54: vmx| Msg_Hint: msg.disk.rawacpi (shown)
Mar 26 04:54:54: vmx| MStat: Creating Stat vm.heartbeat
Mar 26 04:54:54: vmx| DISKUTIL: ide0:0 : toolsVersion = 6530
Mar 26 04:54:54: vmx| TOOLS INSTALL initializing state to IDLE on power on.
Mar 26 04:54:54: vmx| No valid NVRAM file found, will create default NVRAM.
Mar 26 04:54:54: vmx| XINFO X fd is 46
Mar 26 04:54:54: vmx| XINFO depth 24 bpp 32 class 4
Mar 26 04:54:54: vmx| XINFO WARNING: XF86MISC version 0.9
Mar 26 04:54:54: vmx| VT redirected kernel output to /dev/tty1
Mar 26 04:54:54: vmx| USB: Initializing UHCI host controller
Mar 26 04:54:54: vmx| USB: Initializing USB Generic backend
Mar 26 04:54:54: vmx| VMMon_GetkHzEstimate: Calculated 996821 kHz
Mar 26 04:54:54: vmx| VLANCE: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks
Mar 26 04:54:54: vmx| Ethernet0 MAC Address: 00:0c:29:3b:79:36
Mar 26 04:54:54: vmx| VMXNET: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks, dontClusterSize is 128
Mar 26 04:54:54: vmx| E1000: checksum cycles/kB: C=865 asm=710
Mar 26 04:54:54: vmx| VMX_PowerOn: ModuleTable_PowerOn = 1
Mar 26 04:54:54: mks| Async MKS thread is alive
Mar 26 04:54:54: vcpu-0| PShare: enabled 1, scanRate 32, checkRate 16
Mar 26 04:54:54: vcpu-0| guestCpuFeatures = 0x8735e02
Mar 26 04:54:54: vcpu-0| Init modules.
Mar 26 04:54:54: vcpu-0| DISKUTIL: ide0:0 : capacity=78242975
Mar 26 04:54:54: vcpu-0| CPU reset: hard
Mar 26 04:54:54: vmx| Opening sound device for the first time.
Mar 26 04:54:54: vmx| Opened (maybe) sound device for the first time.
Mar 26 04:54:54: vmx| VNET: Notification enabled for Ethernet0
Mar 26 04:54:54: vmx| CDROM:  Implementing mediaChange workaround.
Mar 26 04:54:54: vmx| CDROM:  SEND PACKET API Heuristic active.
Mar 26 04:54:54: vmx| CDROM:  Using SG_IO ioctl for pass-through.
Mar 26 04:54:54: mks| Connecting to window system.
Mar 26 04:54:54: mks| XINFO X fd is 44
Mar 26 04:54:54: mks| XINFO depth 24 bpp 32 class 4
Mar 26 04:54:54: mks| XINFO WARNING: XF86MISC version 0.9
Mar 26 04:54:54: mks| VT redirected kernel output to /dev/tty1
Mar 26 04:54:54: mks| rasterops MMXEXT accelerations enabled
Mar 26 04:54:54: mks| XINFO unsupported XF86VidMode version: 2.2
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 0: 1024x768 flags: 0xa
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 1: 800x600 flags: 0x5
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 2: 640x480 flags: 0xa
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 3: 1024x768 flags: 0x6
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 4: 1024x768 flags: 0xa
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 5: 832x624 flags: 0xa
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 6: 832x624 flags: 0xa
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 7: 800x600 flags: 0x6
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 8: 800x600 flags: 0x5
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 9: 800x600 flags: 0x5
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 10: 800x600 flags: 0x5
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 11: 800x600 flags: 0x5
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 12: 800x600 flags: 0x5
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 13: 800x600 flags: 0x5
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 14: 800x600 flags: 0x5
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 15: 800x600 flags: 0x5
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 16: 800x600 flags: 0x5
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 17: 640x480 flags: 0x6
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 18: 640x480 flags: 0xa
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 19: 640x480 flags: 0xa
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 20: 640x480 flags: 0xa
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 21: 640x480 flags: 0xa
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 22: 640x480 flags: 0xa
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 23: 640x480 flags: 0xa
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 24: 640x480 flags: 0xa
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 25: 640x480 flags: 0xa
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 26: 720x400 flags: 0xa
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 27: 720x400 flags: 0x6
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 28: 720x400 flags: 0x6
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 29: 640x400 flags: 0x6
Mar 26 04:54:54: mks| XINFO XFree86 VidMode 30: 640x350 flags: 0x9
Mar 26 04:54:54: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:54:54: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:54:54: vcpu-0| INTELRDMSR(0x8b) = 0x0000000800000000
Mar 26 04:54:54: vcpu-0| INTELRDMSR(0x17) = 0x6952000000000000
Mar 26 04:54:54: mks| MKS could not find key event for 0x6d up
Mar 26 04:54:54: mks| MKS could not find key event for 0x6d down
Mar 26 04:54:54: vcpu-0| sz=3112928
Mar 26 04:54:54: vcpu-0| vmm32 initialized: Releasebuild-34682. cflags: 0x00000002.01803000.00000054
Mar 26 04:54:55: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0x0) and 0xec000000(0x0)
Mar 26 04:54:55: vcpu-0| PCI OPROM: Asked to map the VBIOS OPROM at 0xfe800000 (size 32768 bytes)
Mar 26 04:54:55: vcpu-0| PCI OPROM: Asked to unmap the VBIOS OPROM
Mar 26 04:54:55: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Mar 26 04:54:55: vcpu-0| PCI OPROM: Asked to map the VLANCE OPROM at 0xfe800000 (size 65536 bytes)
Mar 26 04:54:55: vcpu-0| PCI OPROM: Asked to unmap the VLANCE OPROM
Mar 26 04:54:55: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Mar 26 04:54:55: vcpu-0| PCI OPROM: Asked to map the VBIOS OPROM at 0xfe800000 (size 32768 bytes)
Mar 26 04:54:55: vcpu-0| PCI OPROM: Asked to unmap the VBIOS OPROM
Mar 26 04:54:55: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Mar 26 04:54:55: vcpu-0| SVGA: Registering IOSpace at 0x1400 (0x0)
Mar 26 04:54:55: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Mar 26 04:54:55: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:54:55: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:54:55: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:54:55: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:54:55: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:54:55: vcpu-0| UHCI: Global Reset
Mar 26 04:54:55: vcpu-0| UHCI: HCReset
Mar 26 04:54:55: vcpu-0| UHCI: HCReset
Mar 26 04:54:57: vcpu-0| PCI OPROM: Asked to map the VLANCE OPROM at 0xfe800000 (size 65536 bytes)
Mar 26 04:54:57: vcpu-0| PCI OPROM: Asked to map the VLANCE OPROM at 0xfe800000 (size 65536 bytes)
Mar 26 04:54:57: vcpu-0| PCI OPROM: Asked to unmap the VLANCE OPROM
Mar 26 04:54:57: vcpu-0| VIDE: Curr CHS info cyls: 17475 heads: 15 sects: 63 lba_cap: 78242975
Mar 26 04:54:58: vcpu-0| BIOS-UUID is 56 4d 89 a1 9f 06 e7 38-a6 7f b2 e5 8a 3b 79 36
Mar 26 04:54:59: vcpu-0| DISKUTIL: ide0:0 : toolsVersion = 6530
Mar 26 04:54:59: vcpu-0| DISKUTIL: ide0:0 : toolsVersion = 6530
Mar 26 04:54:59: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:54:59: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 26 04:54:59: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 26 04:54:59: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 26 04:54:59: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 26 04:54:59: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 26 04:54:59: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 26 04:54:59: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 26 04:54:59: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 26 04:55:00: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 26 04:55:00: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 26 04:55:00: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 26 04:55:00: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 26 04:55:00: vcpu-0| Unknown int 10h func 0x2000
Mar 26 04:55:08: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:55:08: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:55:08: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:55:08: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:55:09: vcpu-0| UHCI: Global Reset
Mar 26 04:55:10: vcpu-0| SVGA: Unregistering IOSpace at 0x1400 (0x1400)
Mar 26 04:55:10: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Mar 26 04:55:10: vcpu-0| SVGA: Registering IOSpace at 0x1400 (0x0)
Mar 26 04:55:10: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Mar 26 04:55:10: vcpu-0| CPU reset: soft
Mar 26 04:55:11: vcpu-0| SVGA: Unregistering IOSpace at 0x1400 (0x1400)
Mar 26 04:55:11: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Mar 26 04:55:11: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xe8000000(0xec000000)
Mar 26 04:55:11: vcpu-0| PCI OPROM: Asked to map the VBIOS OPROM at 0xfe800000 (size 32768 bytes)
Mar 26 04:55:11: vcpu-0| PCI OPROM: Asked to unmap the VBIOS OPROM
Mar 26 04:55:11: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xe8000000(0xe8000000)
Mar 26 04:55:11: vcpu-0| PCI OPROM: Asked to map the VLANCE OPROM at 0xfe800000 (size 65536 bytes)
Mar 26 04:55:11: vcpu-0| PCI OPROM: Asked to unmap the VLANCE OPROM
Mar 26 04:55:11: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xe8000000(0xe8000000)
Mar 26 04:55:11: vcpu-0| PCI OPROM: Asked to map the VBIOS OPROM at 0xfe800000 (size 32768 bytes)
Mar 26 04:55:11: vcpu-0| PCI OPROM: Asked to unmap the VBIOS OPROM
Mar 26 04:55:11: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xe8000000(0xe8000000)
Mar 26 04:55:11: vcpu-0| SVGA: Registering IOSpace at 0x1400 (0x0)
Mar 26 04:55:11: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xe8000000(0xe8000000)
Mar 26 04:55:11: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:55:11: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:55:12: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:55:12: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:55:12: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:55:12: vcpu-0| UHCI: Global Reset
Mar 26 04:55:12: vcpu-0| UHCI: HCReset
Mar 26 04:55:12: vcpu-0| UHCI: HCReset
Mar 26 04:55:13: vcpu-0| PCI OPROM: Asked to map the VLANCE OPROM at 0xfe800000 (size 65536 bytes)
Mar 26 04:55:13: vcpu-0| PCI OPROM: Asked to map the VLANCE OPROM at 0xfe800000 (size 65536 bytes)
Mar 26 04:55:13: vcpu-0| PCI OPROM: Asked to unmap the VLANCE OPROM
Mar 26 04:55:13: vcpu-0| VIDE: Curr CHS info cyls: 17475 heads: 15 sects: 63 lba_cap: 78242975
Mar 26 04:55:13: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:55:13: vmx| VMXVmdbCbVmVmxExecState: Exec state change requested to state suspended without reset
Mar 26 04:55:13: vcpu-0| Sync monModules(1).
Mar 26 04:55:13: vcpu-0| Done Sync monModules(1).
Mar 26 04:55:13: vcpu-0| Cpt monModules(2).
Mar 26 04:55:13: vcpu-0| Done Cpt monModules(2).
Mar 26 04:55:13: vmx| DUMPER: Creating checkpoint file ./WindowsXP.vmss
Mar 26 04:55:13: vmx| MM: Renamed /home/shantanu/vmware-windows/564d89a1-9f06-e738-a67f-b2e58a3b7936.vmem to ./WindowsXP.vmem
Mar 26 04:55:15: vmx| Ignoring update request in VGA_Expose (mode change pending).
Mar 26 04:55:15: vmx| Stopping VCPU threads...
Mar 26 04:55:16: mks| Detaching from window system.
Mar 26 04:55:16: mks| Async MKS thread is exiting
Mar 26 04:55:16: vmx| DnD rpc already set to 0
Mar 26 04:55:16: vmx| TOOLS received request in VMX to set option 'enableDnD' -> '0'
Mar 26 04:55:16: vmx| MKS local poweroff
Mar 26 04:55:16: vmx| Lock before MKS lock created.  Early poweroff?
Mar 26 04:55:16: vmx| Unlock before MKS lock created.  Early poweroff?
Mar 26 04:55:16: IO#3| AIOGNRC: thread #3 exiting (242)
Mar 26 04:55:16: IO#0| AIOGNRC: thread #0 exiting (311)
Mar 26 04:55:16: IO#1| AIOGNRC: thread #1 exiting (251)
Mar 26 04:55:16: IO#2| AIOGNRC: thread #2 exiting (275)
Mar 26 04:55:16: vmx| AIOGNRC: asyncOps=1079 syncOps=13 maxPending=3 maxCompleted=3
Mar 26 04:55:16: vmx| vmdbPipe_Streams Couldn't read: OVL_STATUS_EOF
Mar 26 04:55:16: vmx| VMX idle exit
Mar 26 04:55:16: vmx| Flushing VMX VMDB connections
Mar 26 04:55:16: vmx| IPC_exit: disconnecting all threads
Mar 26 04:55:16: vmx| VMX exit.
Mar 26 04:55:16: vmx| AIOMGR-S : stat o=5 r=5 w=0 i=2 br=2262 bw=0[/COLOR]

Any solution guys. :confused:

---

