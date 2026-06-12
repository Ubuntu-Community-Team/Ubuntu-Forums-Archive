---
title: "Lubuntu Start-Up Problem"
date: 2012-01-17
forum: Desktop Environments
---

### Post by Rodney9 on 2012-01-17
Hello, 

When I start [COLOR="Blue"]Lubuntu[/COLOR] sometimes it stops at a black screen showing blue tooth, pulse etc. and goes no further.

I have to use ctrl/alt f3 to get a log-in  and then sudo reboot

I have always had this problem from time to time, but it is happening more often lately, twice this morning.

Is there a way to start the Lubuntu desktop from this command line or better still fix the main problem ?

**Details**
Toshiba Satellite L500/08P Laptop 
Lubuntu 11.10 32bit
3.0.0-14-generic


sudo lshw

```
    description: Notebook
    version: PSLS0A-08P002
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 family=ABCDEFGHIJKLMNOPQRSTUVWXYZ sku=012345678912345678912345678 uuid=74B827DA-2BE9-11DF-85A2-705AB683F14B
  *-core
       description: Motherboard
       product: KSWAA
       vendor: TOSHIBA
       physical id: 0
       version: 1.00
       serial: 0123456789AB
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.90
          date: 12/17/2009
          size: 111KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: Pentium(R) Dual-Core CPU       T4400  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: U2E1
          size: 1200MHz
          capacity: 4096MHz
          width: 64 bits
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm cpufreq
          configuration: cores=2 enabledcores=2 id=0 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 4MiB
             capabilities: burst internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM Synchronous 800 MHz (1.2 ns) [empty]
             product: 8HTF12864HDY-800G1
             vendor: Toshiba
             physical id: 0
             serial: DD456AF3
             slot: M1
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: 64T128020EDL2.5C2
             vendor: Toshiba
             physical id: 1
             serial: 1706DB14
             slot: M2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 2200MHz
          capacity: 2200MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:46 memory:f2800000-f2bfffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f2100000-f21fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:f2504800-f2504bff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:47 memory:f2500000-f2503fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:f4000000-f5ffffff ioport:f0000000(size=33554432)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:80000000-800fffff ioport:f2000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0e:00.0
                logical name: eth0
                version: 02
                serial: 70:5a:b6:83:f1:4b
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:44 ioport:3000(size=256) memory:f2010000-f2010fff memory:f2000000-f200ffff memory:f2020000-f203ffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:f2200000-f22fffff ioport:80600000(size=2097152)
           *-network
                description: Wireless interface
                product: RTL8191SEvB Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:14:00.0
                logical name: wlan0
                version: 10
                serial: b4:82:fe:8f:11:22
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192se driverversion=3.0.0-14-generic firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:19 ioport:4000(size=256) memory:f2200000-f2203fff
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:5000(size=4096) memory:80200000-803fffff ioport:80400000(size=2097152)
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:18a0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18c0(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f2504c00-f2504fff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             logical name: scsi4
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:1818(size=8) ioport:180c(size=4) ioport:1810(size=8) ioport:1808(size=4) ioport:18e0(size=32) memory:f2504000-f25047ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK5055GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: GC00
                serial: Z9TFS6CJS
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000d6f98
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 93d85389-6af7-4719-ad04-b40615aefbc6
                   size: 463GiB
                   capacity: 463GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-10-23 15:36:12 filesystem=ext4 lastmountpoint=/ modified=2012-01-06 12:40:52 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-01-18 05:00:06 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 1911MiB
                   capacity: 1911MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1911MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GT20N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: CT11
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:80100000-801000ff ioport:1c00(size=32)
  *-battery
       description: Lithium Ion Battery
       product: TOSHIBA
       vendor: TOSHIBA
       physical id: 1
       slot: 1st Battery
       capacity: 60000mWh
       configuration: voltage=10.8V

```

Thank You
Rodney

---

### Post by Rex Bouwense on 2012-01-18
You say that you have had this problem for a while and it is getting worse.  Did the problem exist when using the 3.0.0.13 kernel?  I have had a couple of kernel panics with the .14 kernel but nothing that a reboot hasn't "fixed", but nothing like you are experiencing.

What errors are you getting in the boot log?

---

### Post by Rodney9 on 2012-01-18
> **Rex Bouwense said:**
> You say that you have had this problem for a while and it is getting worse.  Did the problem exist when using the 3.0.0.13 kernel?  I have had a couple of kernel panics with the .14 kernel but nothing that a reboot hasn't "fixed", but nothing like you are experiencing.

What errors are you getting in the boot log?

Yes I had this problem randomly since early last year, over several kernels I guess,.

Here is my boot.log from today, of course it started ok today.

```
fsck from util-linux 2.19.1
/dev/sda1: clean, 283595/30408704 files, 11788043/121606656 blocks
 * Starting configure network device security[74G[ OK ]
 * Starting configure network device[74G[ OK ]
 * Starting Bridge socket events into upstart[74G[ OK ]
 * Starting System V initialisation compatibility[74G[ OK ]
 * Starting AppArmor profiles       [80G 
[74G[ OK ]
 * Setting sensors limits       [80G 
[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting configure network device[74G[ OK ]
SpamAssassin Mail Filter Daemon: disabled, see /etc/default/spamassassin
Starting the Network Audio System
Network Audio System Release 1.9.2
Checking for running unattended-upgrades: 
 * Stopping System V initialisation compatibility[74G[ OK ]
 * Starting System V runlevel compatibility[74G[ OK ]
 * Starting CPU interrupts balancing daemon[74G[ OK ]
 * Starting deferred execution scheduler[74G[ OK ]
 * Starting regular background program processing daemon[74G[ OK ]
 * Starting anac(h)ronistic cron[74G[ OK ]
 * Starting save kernel messages[74G[ OK ]
 * Stopping save kernel messages[74G[ OK ]
 * Starting Userspace bootsplash[74G[ OK ]


```

Rodney

---

### Post by Rex Bouwense on 2012-01-18
OK.  That is good that it booted properly.  If it does it again check the log and we shall see what we can deduce from that.

---

### Post by Rodney9 on 2012-01-18
> **Rex Bouwense said:**
> OK.  That is good that it booted properly.  If it does it again check the log and we shall see what we can deduce from that.

Thank You


Rodney

---

### Post by Rodney9 on 2012-01-24
Well It happened again this morning, this is what my boot.log says -

```
fsck from util-linux 2.19.1
/dev/sda1 has been mounted 39 times without being checked, check forced.
/dev/sda1: 310003/30408704 files (0.3% non-contiguous), 12097334/121606656 blocks
 * Starting AppArmor profiles       [106G 
[100G[ OK ]
 * Setting sensors limits       [106G 
[100G[ OK ]
 * Starting mDNS/DNS-SD daemon[100G[ OK ]
 * Starting network connection manager[100G[ OK ]
SpamAssassin Mail Filter Daemon: disabled, see /etc/default/spamassassin
 * Stopping Failsafe Boot Delay[100G[ OK ]
Starting the Network Audio System
```

Is it the 'Sound' that's halting it ???


Rodney

---

### Post by Guilden_NL on 2012-01-24
As I started reading your post and the response, I was thinking either USB or sound.

I had exactly the same problem that appeared to be related to a wonky USB problem that was automagically cured when I added set keycodes for two keys that were driving my new Lubuntu install nuts.

Last time I ran into a sound problem like this was around Hardy or Ibex, though for the Gnome desktop.  I'll search around the threads I posted to and see if I can find the related thread with the cure.

---

### Post by Rex Bouwense on 2012-01-24
Here I thought that perhaps the bad boy went away on its own like the kernel panics that I had.  There have been a couple of kernel updates (two versions of 3.0.0.15 I think, so maybe there is only one).  Is that as far as the boot got, starting network audio system?  So you cannot boot normally at all.

---

### Post by Rodney9 on 2012-01-24
> **Rex Bouwense said:**
> Here I thought that perhaps the bad boy went away on its own like the kernel panics that I had.  There have been a couple of kernel updates (two versions of 3.0.0.15 I think, so maybe there is only one).  Is that as far as the boot got, starting network audio system?  So you cannot boot normally at all.

That's where it stopped, I had to Alt/Ctrl f4 that took to the log-in, then I copied the boot log to my  home directory.


Rodney

---

### Post by Rex Bouwense on 2012-01-28
I have been thinking (I know usual for an old guy like me) and googling and I didn't find anything useful.  If it was the sound, wouldn't there be some error displayed in the boot log and there was not.  Well Rodney, I just know that there is some smart guy or gal out there with the solution.  I'm sorry that it cannot be me right now.  If you could duplicate the error it would obviously be a bug and could report it on launchpad.  Random errors, I don't know.

---

### Post by Rodney9 on 2012-01-28
Thank You Rex.

Hopefully it stays very random and 12.04 will work perfectly I'm sure.

Rodney

---

### Post by Rex Bouwense on 2012-01-28
Fingers crossed here.:)

---

### Post by Theredbaron1834 on 2012-01-29
I have had the exact same problem here, but it was an everytime thing. To boot I had to go in recovery mode, resume boot, log in, and startx.

However, I just fix it less then 10 min ago. I installed Lightdm, made it my default, purged Lxdm, reinstall Lxdm made it my default, purged Lightdm, and installed lubuntu-default-settings (I just used LXDE before). Now it works fine. Don't know what part fixed it, but hopefully it can help you.

Best of luck.

---

