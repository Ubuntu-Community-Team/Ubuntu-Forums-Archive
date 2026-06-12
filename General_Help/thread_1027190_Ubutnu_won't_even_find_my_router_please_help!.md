---
title: "Ubutnu won't even find my router please help!"
date: 2009-01-01
forum: General Help
---

### Post by iPodVision on 2009-01-01
Problem fixed

---

### Post by wmdiem on 2009-01-01
Do what does "iwlist scan" return?

---

### Post by iPodVision on 2009-01-01
Please acknowledge I did see your reply, at the moment I'm uploading a video, ill post the results of iwlist after this video is done uploading! Thanks for your reply also very nice of you for not just viewing!

---

### Post by Ahadiel on 2009-01-01
Paste the outputs of
```
ifconfig -a
```
```
iwconfig
```
and
```
lspci
```

---

### Post by iPodVision on 2009-01-01
> **Ahadiel said:**
> Paste the outputs of
```
ifconfig -a
```
```
iwconfig
```
and
```
lspci
```

How do I post the results? I know I can copy from terminal but how do I post with no internet haha I'm Linux noob as I said.

---

### Post by dcstar on 2009-01-01
> **iPodVision said:**
> How do I post the results? I know I can copy from terminal but how do I post with no internet haha I'm Linux noob as I said.

And how did you post these?

---

### Post by iPodVision on 2009-01-01
> **dcstar said:**
> And how did you post these?

:O Wait I do the commands in CMD Or through Linux? I'm confused.

---

### Post by Ahadiel on 2009-01-01
From the commandline while in Linux?

If you have a USB Drive save the output of the commands and paste them from a computer with internet.

---

### Post by iPodVision on 2009-01-01
> **Ahadiel said:**
> From the commandline while in Linux?

If you have a USB Drive save the output of the commands and paste them from a computer with internet.

Ahh yes usb drive! Thanks for the info ill post the results!

---

### Post by iPodVision on 2009-01-01
Guys it wont copy to my CD says not supported, is there a way to acess ubuntu files through vista?

---

### Post by Ahadiel on 2009-01-01
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by MaindotC on 2009-01-01
> **iPodVision said:**
> Guys it wont copy to my CD says not supported, is there a way to acess ubuntu files through vista?

What happened to the USB drive?  While you're in Ubuntu just save the text file to your My Documents folder or whatever on your Vista partition.

---

### Post by iPodVision on 2009-01-01
> **Ahadiel said:**
> [http://www.fs-driver.org/](http://www.fs-driver.org/)

Heres where you going to stop helping me, how do I setup this thing?

---

### Post by MaindotC on 2009-01-01
> **iPodVision said:**
> Heres where you going to stop helping me, how do I setup this thing?

Get the USB drive but in the odd event you dont, click "download" and I suggest you select the download location to be your desktop.  When it is fully downloaded, double-click the file that was downloaded.  It should be named Ext2IFS_1_11a.exe.  When it finishes installing, you'll probably need to reboot.  WHen you do, open a file explorer and you should now see a new drive in addition to your C: drive or whatever Vister calls it nowadays.  It should be named D: or E:...something like that.  Locate the location of the text file you saved, open it, and copy/paste the contents onto here using "code" tags
```

like this

```

---

### Post by iPodVision on 2009-01-01
[IMG]http://i328.photobucket.com/albums/l354/troyownsyou/wtf.jpg[/IMG]

Is what I get once I install

---

### Post by MaindotC on 2009-01-01
Whatever that is, it's not Ubuntu.  Looks to be a CD you have inserted.  Locate the textfile you have saved on your Ubuntu partition.  I believe Winblows has some type of file search.

---

### Post by Ahadiel on 2009-01-01
When you installed the ext2 driver it should've prompted you to select a drive letter for your Ubuntu partition.

Also, that's (in your screenshot) the recovery partition made by your OEM in case you need to reinstall Windows.

---

### Post by iPodVision on 2009-01-01
> **strAlan said:**
> Whatever that is, it's not Ubuntu.  Looks to be a CD you have inserted.  Locate the textfile you have saved on your Ubuntu partition.  I believe Winblows has some type of file search.
Do you mind getting on AIM this would be quicker? I installed the fs driver thing, and that's what came out, I have no disk inserted into my computer right now.

---

### Post by iPodVision on 2009-01-01
> **Ahadiel said:**
> When you installed the ext2 driver it should've prompted you to select a drive letter for your Ubuntu partition.

Also, that's (in your screenshot) the recovery partition made by your OEM in case you need to reinstall Windows.

Wouldnt the partition be located right next to my c drive? I didnt burn ubuntu to a disk I used wubi to install, so there is nothing by my c drive

---

### Post by 3rdalbum on 2009-01-01
> **iPodVision said:**
> Wouldnt the partition be located right next to my c drive? I didnt burn ubuntu to a disk I used wubi to install, so there is nothing by my c drive

PLEASE use a USB drive to transfer the results of those commands. The driver you installed on Windows won't do anything because Wubi doesn't actually partition your hard disk.

---

### Post by iPodVision on 2009-01-01
> **3rdalbum said:**
> PLEASE use a USB drive to transfer the results of those commands. The driver you installed on Windows won't do anything because Wubi doesn't actually partition your hard disk.
I dont have a usb stick =/, could my psp be used as one?

---

### Post by iPodVision on 2009-01-01
```
troy@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

troy@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:80:1e:0f:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

pan0      Link encap:Ethernet  HWaddr de:2e:14:f3:5a:a8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

troy@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


```

FINNALY

---

### Post by wmdiem on 2009-01-01
does 
lsmod | grep ath 
print anything?

Assuming it doesn't print something like ath_pci you are probably going to need to install madwifi. 
The question is whether you have an AR2424 (AR5006 chipset) or an AR2425 (AR5007 chipset) because the AR5007 is (well, at least it was a few months ago when I set my computer up) only supported by a special snapshot of madwifi that you have to compile, c.f.: [http://ubuntuforums.org/showthread.php?t=795984&highlight=compiling+madwifi](http://ubuntuforums.org/showthread.php?t=795984&highlight=compiling+madwifi)

---

### Post by MaindotC on 2009-01-01
> **3rdalbum said:**
> The driver you installed on Windows won't do anything because Wubi doesn't actually partition your hard disk.

Wow I didn't know this. I learn something new everyday.

[quote=iPodVision]06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)[/quote]
This is your wireless card and it seems Ubuntu detects it properly.  In the ifconfig output, eth0 is your wired network connection (02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)) and pan0 seems to be your wireless network card.  You didn't post "iwlist scan" but it seems that even if you tried your wireless card would not scan for wireless networks.

I thought if you didn't have the wireless driver installed then you wouldn't even get a "pan0" in your ifconfig but try wmdiem's advice.  Open Synaptic and search for "madwifi".

---

### Post by wmdiem on 2009-01-01
pan0 should be a bluetooth personal area network. 
I recommend that you find out the exact model number of your wireless card, and then spend a little time on Google to see which chipset it has. Then you should be able to figure out which driver you need. 
also, if you want to see how it is configured now you can use 
sudo lshw 
and look for the card's entry to find out what module (if any) is being used to control it.

---

### Post by MaindotC on 2009-01-01
[quote=wmdiem]pan0 should be a bluetooth personal area network. [/quote]
Thanks, wmdiem.  I should have known that :D

---

### Post by MaindotC on 2009-01-02
I'm talking to OP on IM.  He didn't even use his wired connection to download updates.  I have him running Update Manager now.  After a reboot if he doesn't have the proper drivers I'll have him d/l madwifi.  Newbs these days.

---

### Post by wmdiem on 2009-01-02
You do want to be careful since AR242x may or may not be supported by madwifi depending on what the x stands for. If it isn't it will require either a custom compiled version ([http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)) or just using ndiswrapper although there may be more options now than there were when I was setting mine up (ath5k?).

---

### Post by iPodVision on 2009-01-02
Yah damn newbs these days, well str is helping me a lot =] so far so good!

---

### Post by iPodVision on 2009-01-02
Guys I installed every update and it still wont pick up a signal! Request any command I'm in ubuntu right now wired. So please help.

---

### Post by wmdiem on 2009-01-02
okay, do sudo lshw to see what is controling the card

---

### Post by iPodVision on 2009-01-02
I did try ndiswrapper so idk if that will affect this output. I disabled my other driver and got a .inf file, actually here's the exact thread I followed: [http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)


And here is the code

```
ubuntu                    
    description: Notebook
    product: VGN-NR110E
    vendor: Sony Corporation
    version: C3LQ3U14
    serial: 28270534-3040253
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=439AA8C0-793E-11DC-80B3-001A801E0F22
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
       slot: &#65533;&#65533;@
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0130J9 (07/18/2007)
          size: 100KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
          serial: N/A
          slot: N/A
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3 Cache
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM
             physical id: 0
             slot: SODIMM1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: SODIMM
             physical id: 1
             slot: SODIMM2
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8039 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 14
                serial: 00:1a:80:1e:0f:22
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.0.192 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix cap_list
                configuration: latency=0
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:08:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 3.1
                bus info: pci@0000:08:03.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=3 module=ohci1394
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 3.2
                bus info: pci@0000:08:03.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AW-G540A
                vendor: SONY
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.W0
                serial: [SONY    DVD RW AW-G540A 1.W0 Jul03,2007
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: Hitachi HTS54161
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: SBDO
                serial: SB3DA1EWHHE3JE
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=62abe731
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 0ccdbad6-7ac5-f843-9257-ff4c57eaaaee
                   size: 7544MiB
                   capacity: 7546MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2007-08-27 02:40:25 filesystem=ntfs label=Recovery state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /host
                   logical name: /boot
                   version: 3.1
                   serial: fe65abfa-dffb-3a48-b9b9-de972c1ca421
                   size: 104GiB
                   capacity: 104GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=512 created=2008-12-26 04:15:02 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:9d:8b:0c:61:5c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by iPodVision on 2009-01-02
> **iPodVision said:**
> I did try ndiswrapper so idk if that will affect this output. I disabled my other driver and got a .inf file, actually here's the exact thread I followed: [http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)



By the way guys, that LINK I SAID DID NOT FIX MY PROBLEM

---

### Post by wmdiem on 2009-01-02
right, that looks like it still doesn't have a module running. try lsmod

---

### Post by iPodVision on 2009-01-02
Problem fixed

---

### Post by MaindotC on 2009-01-03
How?

---

