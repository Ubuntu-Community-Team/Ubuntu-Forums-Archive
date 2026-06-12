---
title: "Can Anyone Help With Minecraft and the X205TA?   :)"
date: 2018-06-15
forum: Gaming &amp; Leisure
---

### Post by colbaltphoenix on 2018-06-15
Hi everyone!   First, I would like to thank all of you who worked to make Ubuntu and the ASUS X205TA a success, and I can report that Minecraft now works without issue (with re-adding the Java Certs, and deleting the "IncrementalCMS" "UseConicMarkSweep" options in the Minecraft Launcher).   But now I have an issue, and I can confirm this occurs with Firefox and Chrome as well.   The issue is that the Keyboard will stop working randomly, it seems.   First, what I have tried:

Reinstalling the Xorg input Drivers

Editing GRUB2 to have the option "intel_idle.max_cstate=1"

Decreasing RAM usage, both via the JVM options, and through using IceWM

Any ideas guys?   :)   This is the only thing I'm having trouble with (aside from running VMs on @harryharryharry 's custom Kernel, but, as I've only 2 Gigs of RAM, I don't really care.)   I REALLY appreciate any help, guys.   :)   And thank you, @harryharryharry for the awesome Sound Kernel patch!   :D

Oh, and here's my Hardware info:

```
    description: Notebook    product: X205TA (ASUS-NotebookSKU)
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: EANLBC07754842E
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: boot=normal chassis=notebook family=X sku=ASUS-NotebookSKU uuid=B0BE1300-4E0E-2F33-FFFF-6CFAA732AB0C
  *-core
       description: Motherboard
       product: X205TA
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: X205TA.212
          date: 09/04/2015
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 2GiB
          capabilities: ecc
          configuration: errordetection=multi-bit-ecc
        *-bank
             description: DIMM DDR3 1333 MHz (0.8 ns)
             product: Array1_PartNumber0
             vendor: A1_Manufacturer0
             physical id: 0
             serial: A1_SerNum0
             slot: A1_DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cache:0
          description: L1 cache
          physical id: f
          slot: CPU Internal L1
          size: 224KiB
          capacity: 224KiB
          capabilities: internal write-back
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 10
          slot: CPU Internal L2
          size: 1MiB
          capacity: 1MiB
          capabilities: internal write-back unified
          configuration: level=2
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU  Z3735F @ 1.33GHz
          vendor: Intel Corp.
          physical id: 11
          bus info: cpu@0
          version: Intel(R) Atom(TM) CPU Z3735F @ 1.33GHz
          slot: SOCKET 0
          size: 512MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 83MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb pti tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
          configuration: cores=4 enabledcores=4 threads=4
     *-pci
          description: Host bridge
          product: Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0f
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:33 memory:90000000-903fffff memory:80000000-8fffffff ioport:1000(size=8) memory:c0000-dffff
        *-usb
             description: USB controller
             product: Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 0f
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:30 memory:90800000-9080ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.15.0-23-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb:0
                   description: Video
                   product: USB Camera
                   vendor: 04081-00092400E9669X
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.12
                   serial: 200901010001
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:1
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 2
                   bus info: usb@1:2
                   version: 32.98
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb
                      description: Mass storage device
                      product: USB DISK 2.0
                      physical id: 1
                      bus info: usb@1:2.1
                      logical name: scsi0
                      version: 1.00
                      serial: 0708282D211C7492
                      capabilities: usb-2.00 scsi emulated scsi-host
                      configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
                    *-disk
                         description: SCSI Disk
                         product: USB DISK 2.0
                         physical id: 0.0.0
                         bus info: scsi@0:0.0.0
                         logical name: /dev/sda
                         version: PMAP
                         serial: 077409822080
                         size: 14GiB (15GB)
                         capabilities: removable
                         configuration: ansiversion=4 logicalsectorsize=512 sectorsize=512
                       *-medium
                            physical id: 0
                            logical name: /dev/sda
                            size: 14GiB (15GB)
                            capabilities: partitioned partitioned:dos
                            configuration: signature=000db77f
                          *-volume:0
                               description: Windows FAT volume
                               vendor: MSWIN4.1
                               physical id: 1
                               logical name: /dev/sda1
                               logical name: /media/adam/F6E5-9812
                               version: FAT32
                               serial: f6e5-9812
                               size: 1859MiB
                               capacity: 1861MiB
                               capabilities: primary fat initialized
                               configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
                          *-volume:1
                               description: Windows FAT volume
                               vendor: mkfs.fat
                               physical id: 2
                               logical name: /dev/sda2
                               logical name: /media/adam/4D31-B60C
                               version: FAT32
                               serial: 4d31-b60c
                               size: 13GiB
                               capacity: 13GiB
                               capabilities: primary fat initialized
                               configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.15.0-23-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.15
                capabilities: usb-3.00
                configuration: driver=hub slots=1 speed=5000Mbit/s
        *-generic
             description: Encryption controller
             product: Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:43 memory:90700000-907fffff memory:90600000-906fffff
        *-isa
             description: ISA bridge
             product: Atom Processor Z36xxx/Z37xxx Series Power Control Unit
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 6c:fa:a7:32:ab:0c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmfmac driverversion=6.10.190.55 firmware=01-6cb01dcc ip=192.168.1.12 multicast=yes wireless=IEEE 802.11
```

---

### Post by wildmanne39 on 2018-06-15
*Thread moved to **Gaming & Leisure for a more appropriate fit**.*

---

### Post by colbaltphoenix on 2018-06-15
I'm sorry about that...   :)

---

### Post by wildmanne39 on 2018-06-15
No apologies needed!

---

### Post by thenailedone on 2018-06-15
> **colbaltphoenix said:**
> But now I have an issue, and I can confirm this occurs with Firefox and Chrome as well.
So you don't actually say what the issue is...?

---

### Post by colbaltphoenix on 2018-06-15
Ok!   :)

---

### Post by colbaltphoenix on 2018-06-15
@thenailedone Wow...   :O   I go to all that trouble to be detailed and helpful, but I forgot to actually SAY what the issue was!   XD   Sorry, my bad...   :)

---

### Post by thenailedone on 2018-06-16
Well from the OP edit it seems your keyboard stops randomly working in Firefox and Chrome... is it only in browsers or in other applications also?

---

### Post by colbaltphoenix on 2018-06-16
@thenailedone No, it only happens in Browsers, or in Minecraft.   :)

---

### Post by colbaltphoenix on 2018-06-16
@thenailedone I should also mention that the Battery icon suddenly acts as if there is no Battery, and it just happened about 3 Minutes ago while I was playing Minecraft.   :(   I had to reboot.

---

### Post by colbaltphoenix on 2018-06-16
Okay, it happened again.   I had a USB Keyboard lying around, and I plugged it in, opened Guake, and put the Grep output into a Text File.   :)   Here is what I think may be causing the problem.

```
[ 7386.241094] i2c_designware 80860F41:00: i2c_dw_xfer_msg: invalid message length[ 7386.241168] i2c i2c-0: i2c read failed
[ 7386.266104] i2c_designware 80860F41:00: timeout waiting for bus ready
[ 7386.266114] i2c i2c-0: i2c read failed
[ 7386.293992] i2c_designware 80860F41:00: timeout waiting for bus ready
[ 7386.294002] i2c i2c-0: i2c read failed
[ 7386.317932] i2c_designware 80860F41:00: timeout waiting for bus ready
[ 7386.317952] i2c i2c-0: i2c read failed
[ 7386.340426] i2c_designware 80860F41:00: timeout waiting for bus ready
[ 7386.340449] i2c i2c-0: i2c read failed
[ 7386.374278] i2c_designware 80860F41:00: timeout waiting for bus ready
[ 7386.374289] i2c i2c-0: i2c read failed
[ 7386.397263] i2c_designware 80860F41:00: timeout waiting for bus ready
[ 7386.397281] i2c i2c-0: i2c read failed
[ 7386.421676] i2c_designware 80860F41:00: timeout waiting for bus ready
[ 7386.421690] i2c i2c-0: i2c read failed
[ 7392.570277] i2c_designware 80860F41:00: timeout waiting for bus ready
[ 7393.797865] i2c_designware 80860F41:00: timeout waiting for bus ready
[ 7395.988620] i2c_designware 80860F41:00: timeout waiting for bus ready
[ 7446.435416] i2c_designware 80860F41:00: timeout waiting for bus ready
```

Does this help?   :)   Thanks for the effort put into this guys.   I really appreciate it.   :)

---

### Post by thenailedone on 2018-06-18
This is above my pay grade. On my desktop I have often experienced strange issues related to my keyboard and mouse due to the chipset I have any the way USB 2 and 3 seem to interact. I never got a solution except to remove and insert the devices (sometimes switching between USB 2 and 3 and visa versa or using a different OS (patience is not a virtue of mine).

Hopefully someone will come along with more insight.

---

