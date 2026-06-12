---
title: "Computer wont boot Ubuntu"
date: 2009-05-16
forum: General Help
---

### Post by jainfo on 2009-05-16
please help im very new to this, just installed ubuntu 9.04 jaunty jackalope but it wont boot. the livecd works, please help

[apparently the problem was incredibly simple and for some reason when i installed the new harddrive it was disabled. an incredibly dumb and easily overlooked mistake, definitely something to learn from!]

-note- everyone was very helpful and quick to respond, this seems like a forum i can definitely stick with, THANKS AGAIN GUYS! -

---

### Post by tommcd on 2009-05-16
You need to provide more info.
Did the install go ok and complete successfully?
What kind of computer is this? Can you post the specs, including graphics card and motherboard chipset?
Is Ubuntu the only operating system on the computer? Or is it a dual boot with Windows?
And most importantly, what *exactly* happens when you try to boot Ubuntu???

And welcome to the Ubuntu forums!

---

### Post by hyperdude111 on 2009-05-16
If you have windows installed you could try wubi until you are ready to move to a partition. 

On your original question we need more info 
eg. Does grub show up
Did the install complete successfully
Full hardware info etc

---

### Post by jainfo on 2009-05-17
okay this is going to be a lot to read but i dont know what exactly info is needed. yes the install said sucessfull, i chose install over entire disk, brandnew westerndigital notebook harddrive. gnub does not show up when i turn on computer, without livecd in drive it says something like

pxe media test failure, check cable
 exiting pxe rom 

something along those lines. my comp specs,( AND THANKS AGAIN FOR TAKING THE TIME TO READ AND HELP):
   id:ubuntu
       description: Notebook     product: Satellite A75     vendor: TOSHIBA     version: PSA70U-09700E     serial: 94335853K     width: 32 bits     capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp     configuration: boot=oem-specific chassis=notebook cpus=1 uuid=4E74769B-8836-11D9-BB3D-000FB05B4E97  
                 id:core
          description: Motherboard        product: EDW10        vendor: TOSHIBA        physical id: 0
        version: Null        serial: 0123456789AB        slot: SVGA-Out      
                          id:firmware
             description: BIOS           vendor: TOSHIBA           physical id: 0
           version: V1.50 (11/16/2004)           size: 104KiB           capacity: 448KiB           capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification         
        
                          id:cpu
             description: CPU           product: Mobile Intel(R) Pentium(R) 4 CPU 3.06GHz           vendor: Intel Corp.           physical id: 4
           bus info: cpu@0
           version: 15.3.4           serial: 0000-0F34-0000-0000-0000-0000           slot: NWD           size: 1867MHz           capacity: 3200MHz           width: 32 bits           capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl est tm2 cid xtpr cpufreq           configuration: id=1         
                                   id:cache:0
                description: L1 cache              physical id: a
              slot: L1 Cache              size: 16KiB              capacity: 16KiB              capabilities: asynchronous internal write-back            
           
                                   id:cache:1
                description: L2 cache              physical id: b
              slot: L2 Cache              size: 1MiB              capabilities: burst internal write-back            
           
                                   id:logicalcpu:0
                description: Logical CPU              physical id: 1.1
              width: 32 bits              capabilities: logical            
           
                                   id:logicalcpu:1
                description: Logical CPU              physical id: 1.2
              width: 32 bits              capabilities: logical            
           
        
                          id:memory
             description: System Memory           physical id: 16
           slot: System board or motherboard           size: 1536MiB         
                                   id:bank:0
                description: SODIMM DDR Synchronous 166 MHz (6.0 ns) [empty]              physical id: 0
              slot: JP21              clock: 166MHz (6.0ns)            
           
                                   id:bank:1
                description: SODIMM DDR Synchronous 166 MHz (6.0 ns) [empty]              physical id: 1
              slot: JP21              clock: 166MHz (6.0ns)            
           
                                   id:bank:2
                description: SODIMM DDR Synchronous 166 MHz (6.0 ns)              physical id: 2
              slot: JP21              size: 512MiB              width: 64 bits              clock: 166MHz (6.0ns)            
           
                                   id:bank:3
                description: SODIMM DDR Synchronous 166 MHz (6.0 ns)              physical id: 3
              slot: JP20              size: 1GiB              width: 64 bits              clock: 166MHz (6.0ns)            
           
        
                          id:pci
             description: Host bridge           product: RS300 Host Bridge           vendor: ATI Technologies Inc           physical id: 100
           bus info: pci@0000:00:00.0
           version: 02           width: 32 bits           clock: 66MHz           configuration: driver=agpgart-ati latency=64 module=ati_agp         
                                   id:pci:0
                description: PCI bridge              product: Radeon 9100 IGP AGP Bridge              vendor: ATI Technologies Inc              physical id: 1
              bus info: pci@0000:00:01.0
              version: 00              width: 32 bits              clock: 66MHz              capabilities: pci bus_master            
                                            id:[COLOR=gray]display[/COLOR]
                   description: VGA compatible controller                 product: RS300M AGP [Radeon Mobility 9100IGP]                 vendor: ATI Technologies Inc                 physical id: 5
                 bus info: pci@0000:01:05.0
                 version: 00                 width: 32 bits                 clock: 66MHz                 capabilities: agp agp-3.0 pm bus_master cap_list                 configuration: latency=66 mingnt=8               
              
           
                                   id:usb:0
                description: USB Controller              product: OHCI USB Controller #1              vendor: ATI Technologies Inc              physical id: 13
              bus info: pci@0000:00:13.0
              version: 01              width: 32 bits              clock: 66MHz              capabilities: bus_master              configuration: driver=ohci_hcd latency=64            
           
                                   id:usb:1
                description: USB Controller              product: OHCI USB Controller #2              vendor: ATI Technologies Inc              physical id: 13.1
              bus info: pci@0000:00:13.1
              version: 01              width: 32 bits              clock: 66MHz              capabilities: bus_master              configuration: driver=ohci_hcd latency=64            
           
                                   id:usb:2
                description: USB Controller              product: EHCI USB Controller              vendor: ATI Technologies Inc              physical id: 13.2
              bus info: pci@0000:00:13.2
              version: 01              width: 32 bits              clock: 66MHz              capabilities: pm bus_master cap_list              configuration: driver=ehci_hcd latency=64 module=ehci_hcd            
           
                                   id:serial
                description: SMBus              product: SMBus              vendor: ATI Technologies Inc              physical id: 14
              bus info: pci@0000:00:14.0
              version: 18              width: 32 bits              clock: 66MHz              configuration: driver=piix4_smbus latency=0 module=i2c_piix4            
           
                                   id:ide
                description: IDE interface              product: Dual Channel Bus Master PCI IDE Controller              vendor: ATI Technologies Inc              physical id: 14.1
              bus info: pci@0000:00:14.1
              logical name: scsi0
              logical name: scsi1
              version: 00              width: 32 bits              clock: 33MHz              capabilities: ide bus_master emulated              configuration: driver=pata_atiixp latency=64            
                                            id:disk
                   description: ATA Disk                 product: WDC WD1600BEVE-0                 vendor: Western Digital                 physical id: 0
                 bus info: scsi@0:0.0.0
                 logical name: /dev/sda
                 version: 01.0                 serial: WD-WXHZ08023435                 size: 149GiB (160GB)                 capabilities: partitioned partitioned:dos                 configuration: ansiversion=5 signature=00032812               
                                                     id:volume:0
                      description: EXT3 volume                    vendor: Linux                    physical id: 1
                    bus info: scsi@0:0.0.0,1
                    logical name: /dev/sda1
                    version: 1.0                    serial: 9301c661-ee36-4f3b-8f56-cf0e9e76c009                    size: 145GiB                    capacity: 145GiB                    capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized                    configuration: created=2009-05-16 02:34:21 filesystem=ext3 modified=2009-05-16 02:45:56 mounted=2009-05-16 02:36:07 state=clean                  
                 
                                                     id:volume:1
                      description: Extended partition                    physical id: 2
                    bus info: scsi@0:0.0.0,2
                    logical name: /dev/sda2
                    size: 4047MiB                    capacity: 4047MiB                    capabilities: primary extended partitioned partitioned:extended                  
                                                              id:logicalvolume
                         description: Linux swap / Solaris partition                       physical id: 5
                       logical name: /dev/sda5
                       capacity: 4047MiB                       capabilities: nofs                     
                    
                 
              
                                            id:cdrom
                   description: DVD reader                 product: DVD-ROM SD-R2512                 vendor: TOSHIBA                 physical id: 1
                 bus info: scsi@1:0.0.0
                 logical name: /dev/cdrom
                 logical name: /dev/cdrw
                 logical name: /dev/dvd
                 logical name: /dev/scd0
                 logical name: /dev/sr0
                 logical name: /cdrom
                 version: 1420                 capabilities: removable audio cd-r cd-rw dvd                 configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready               
                                                     id:medium
                      physical id: 0
                    logical name: /dev/cdrom
                    logical name: /cdrom
                    configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted                  
                 
              
           
                                   id:isa
                description: ISA bridge              product: ATI Technologies Inc              vendor: ATI Technologies Inc              physical id: 14.3
              bus info: pci@0000:00:14.3
              version: 00              width: 32 bits              clock: 66MHz              capabilities: isa bus_master              configuration: latency=0            
           
                                   id:pci:1
                description: PCI bridge              product: IXP200 3COM 3C920B Ethernet Controller              vendor: ATI Technologies Inc              physical id: 14.4
              bus info: pci@0000:00:14.4
              version: 00              width: 32 bits              clock: 66MHz              capabilities: pci bus_master            
                                            id:network:0
                   description: Wireless interface                 product: Atheros AR5001X+ Wireless Network Adapter                 vendor: Atheros Communications Inc.                 physical id: 2
                 bus info: pci@0000:02:02.0
                 logical name: wmaster0
                 version: 01                 serial: 00:90:96:f6:86:ee                 width: 32 bits                 clock: 33MHz                 capabilities: pm bus_master cap_list logical ethernet physical wireless                 configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.78 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg               
              
                                            id:network:1
                   description: Ethernet interface                 product: RTL-8139/8139C/8139C+                 vendor: Realtek Semiconductor Co., Ltd.                 physical id: 3
                 bus info: pci@0000:02:03.0
                 logical name: eth0
                 version: 10                 serial: 00:0f:b0:5b:4e:97                 size: 10MB/s                 capacity: 100MB/s                 width: 32 bits                 clock: 33MHz                 capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation                 configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s               
              
                                            id:pcmcia
                   description: CardBus bridge                 product: CB1410 Cardbus Controller                 vendor: ENE Technology Inc                 physical id: 4
                 bus info: pci@0000:02:04.0
                 version: 01                 width: 32 bits                 clock: 33MHz                 capabilities: pcmcia bus_master cap_list                 configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket               
              
           
                                   id:multimedia
                description: Multimedia audio controller              product: IXP150 AC'97 Audio Controller              vendor: ATI Technologies Inc              physical id: 14.5
              bus info: pci@0000:00:14.5
              version: 00              width: 32 bits              clock: 66MHz              capabilities: bus_master              configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp            
           
                                   id:communication
                description: Modem              product: IXP AC'97 Modem              vendor: ATI Technologies Inc              physical id: 14.6
              bus info: pci@0000:00:14.6
              version: 01              width: 32 bits              clock: 66MHz              capabilities: bus_master              configuration: driver=ATI IXP MC97 controller latency=64 mingnt=2 module=snd_atiixp_modem            
           
        
     
                 id:battery
          description: Lithium Ion Battery        product: PA3383U        vendor: TOSHIBA        physical id: 1
        version: 01/01/2004        serial: 3658Q        slot: 1st Battery        capacity: 3900mWh        configuration: voltage=14.8V      
     
                 id:[COLOR=gray]network[/COLOR]
          description: Ethernet interface        physical id: 2
        logical name: pan0
        serial: d2:82:53:1a:47:54        capabilities: ethernet physical        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by tommcd on 2009-05-18
> **jainfo said:**
>  gnub does not show up when i turn on computer, without livecd in drive it says something like

Since Ubutnu is the only operating system on the computer, the grub menu is not visible by default. To see the grub menu, hit the **Esc** key as the computer boots. It should show you the option for booting Ubuntu, as well as the Ubuntu recovery mode option.
> **jainfo said:**
> 
pxe media test failure, check cable
 exiting pxe rom 

The "media failure, check cable" looks like the hard drive may not be connected properly. You said it is a brand new hard drive. Was this a replacement hard drive for the laptop?
The first thing I would do is boot the computer and hit the Esc key. If you do not even get the grub menu, but instead get the "pxe media test failure, check cable" message, I would open up the laptop and make sure the power and data cables are connected properly and are not loose.

EDIT: Also, check the BIOS on the laptop and make sure it is set to boot from the hard drive. See this:
[http://laptopforums.toshiba.com/t5/General-Technology/PXE-E61-media-test-failure-check-cable/td-p/33394;jsessionid=695EF26A721A6B3F4E71800DB12640B7](http://laptopforums.toshiba.com/t5/General-Technology/PXE-E61-media-test-failure-check-cable/td-p/33394;jsessionid=695EF26A721A6B3F4E71800DB12640B7)
also:
[http://www.pcguide.com/vb/archive/index.php/t-59713.html](http://www.pcguide.com/vb/archive/index.php/t-59713.html)

---

