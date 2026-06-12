---
title: "Why does Hardy boot slowly?"
date: 2009-03-16
forum: General Help
---

### Post by sgissinger on 2009-03-16
Hi
Now I don't know if this is just for me but when I upgraded to HH about 5 months ago, the booting time considerably increased, and instead of the nice Ubuntu logo loading bar, I got the boot-loading monitor (Reading files needed to boot... Done). It didn't bothered me at first but now that I come to think about it, this can't be very hard to fix can it? I found various solutions on the forums but having experienced the touchiness of GRUB, I prefer not to try anything stupid.
Anyone has an idea?
Here is my menu.lst file :
> 
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color blue whit/blue white white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=59acbccf-8a74-44f1-b8e4-7a98cdd41688 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=791 quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.22-14-generic, sgissinger.laptop
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=59acbccf-8a74-44f1-b8e4-7a98cdd41688 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode), sgissinger.laptop
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=59acbccf-8a74-44f1-b8e4-7a98cdd41688 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+, sgissinger.laptop
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional, sgissinger.laptop
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Thanks

---

### Post by Yashiro on 2009-03-16
The splash is already enabled in your Grub file. If the splash screen isn't working when you boot up the problem is not with Grub.

---

### Post by philinux on 2009-03-16
Either look in dmesg for hangs or install bootchart from the repo.

Try disconnecting any usb stuff aprt from keyboard and mouse.

---

### Post by sgissinger on 2009-03-17
Ok thanks, I'll give it a try.

---

### Post by sgissinger on 2009-03-17
So I tried installing bootchart but I don't see what it is supposed to do really, and since I'm a noob (only been using linux for a year or so), I don't know what I'm supposed to do with dmesg. I'm using a laptop computer so I naturally booted up without any usb devices plugged in many many times. Thanks for the help, I still need it!

---

### Post by philinux on 2009-03-18
Ok maybe you googled and found the answers. In case you didn't look here.
[http://ubuntuforums.org/showthread.php?t=868189](http://ubuntuforums.org/showthread.php?t=868189)

You can use the file manager to navigate to /var/log/bootchart and display any png image files bootchart created. You could upload one to.

For dmesg open a terminal and use the command dmesg. Scroll mback though and see if can see where the process hangs by the timestamps on the left.

---

### Post by sgissinger on 2009-03-18
Well thanks, but bootchart doesnt seem to work very well : even after reinstall, I still cant find anything in /var/log/bootchart...
As to dmesg, here's what I get :
> [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff50000 (usable)
[    0.000000]  BIOS-e820: 000000007ff50000 - 000000007ff67000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff67000 - 000000007ff79000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff80000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 524112) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524112
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524112
[    0.000000] On node 0 totalpages: 524112
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292434 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6DF0 checksum 0
[    0.000000] ACPI: RSDP 000F6DF0, 0024 (r2 IBM   )
[    0.000000] ACPI: XSDT 7FF5A6CD, 004C (r1 IBM    TP-1R        3140  LTP        0)
[    0.000000] ACPI: FACP 7FF5A800, 00F4 (r3 IBM    TP-1R        3140 IBM         1)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20070126]
[    0.000000] ACPI: DSDT 7FF5A9E7, C4D5 (r1 IBM    TP-1R        3140 MSFT  100000E)
[    0.000000] ACPI: FACS 7FF78000, 0040
[    0.000000] ACPI: SSDT 7FF5A9B4, 0033 (r1 IBM    TP-1R        3140 MSFT  100000E)
[    0.000000] ACPI: ECDT 7FF66EBC, 0052 (r1 IBM    TP-1R        3140 IBM         1)
[    0.000000] ACPI: TCPA 7FF66F0E, 0032 (r1 IBM    TP-1R        3140 PTL         1)
[    0.000000] ACPI: BOOT 7FF66FD8, 0028 (r1 IBM    TP-1R        3140  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7f800000)
[    0.000000] Built 1 zonelists.  Total pages: 520018
[    0.000000] Kernel command line: root=UUID=59acbccf-8a74-44f1-b8e4-7a98cdd41688 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (02014000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1694.582 MHz processor.
[    2.790699] Console: colour VGA+ 80x25
[    2.791305] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    2.791905] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    2.918694] Memory: 2067092k/2096448k available (2015k kernel code, 28112k reserved, 915k data, 364k init, 1178944k highmem)
[    2.918705] virtual kernel memory layout:
[    2.918706]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    2.918707]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    2.918709]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    2.918710]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    2.918711]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    2.918712]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[    2.918714]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[    2.918717] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    2.918778] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    2.998769] Calibrating delay using timer specific routine.. 3391.43 BogoMIPS (lpj=6782863)
[    2.998813] Security Framework v1.0.0 initialized
[    2.998826] SELinux:  Disabled at boot.
[    2.998842] Mount-cache hash table entries: 512
[    2.999033] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[    2.999048] CPU: L1 I cache: 32K, L1 D cache: 32K
[    2.999051] CPU: L2 cache: 2048K
[    2.999054] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
[    2.999068] Compat vDSO mapped to ffffe000.
[    2.999084] Checking 'hlt' instruction... OK.
[    3.014951] SMP alternatives: switching to UP code
[    3.015300] Freeing SMP alternatives: 11k freed
[    3.015633] Early unpacking initramfs... done
[    3.358476] ACPI: Core revision 20070126
[    3.358590] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    3.362774] ACPI: setting ELCR to 0200 (from 0800)
[    3.372988] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 06
[    3.372994] SMP motherboard not detected.
[    3.372996] Local APIC not detected. Using dummy APIC emulation.
[    3.373034] Brought up 1 CPUs
[    3.373148] Booting paravirtualized kernel on bare hardware
[    3.373201] Time: 23:31:19  Date: 02/18/109
[    3.373224] NET: Registered protocol family 16
[    3.373302] EISA bus registered
[    3.373313] ACPI: bus type pci registered
[    3.373473] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=8
[    3.373475] PCI: Using configuration type 1
[    3.373477] Setting up standard PCI resources
[    3.377067] ACPI: EC: Found ECDT
[    3.385301] ACPI: Interpreter enabled
[    3.385303] ACPI: (supports S0 S3 S4 S5)
[    3.385320] ACPI: Using PIC for interrupt routing
[    3.392008] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[    3.392048] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    3.392054] PCI: Probing PCI hardware (bus 00)
[    3.392408] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    3.392411] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[    3.392878] PCI: Transparent bridge - 0000:00:1e.0
[    3.392983] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    3.393036] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    3.393060] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    3.396532] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    3.396719] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    3.396905] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    3.397090] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    3.397260] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    3.397431] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    3.397601] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    3.397792] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    3.398047] ACPI: Power Resource [PUBS] (on)
[    3.398059] Linux Plug and Play Support v0.97 (c) Adam Belay
[    3.398068] pnp: PnP ACPI init
[    3.398075] ACPI: bus type pnp registered
[    3.401445] pnp: PnP ACPI: found 13 devices
[    3.401448] ACPI: ACPI bus type pnp unregistered
[    3.401451] PnPBIOS: Disabled by ACPI PNP
[    3.401492] PCI: Using ACPI for IRQ routing
[    3.401495] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    3.412456] NET: Registered protocol family 8
[    3.412458] NET: Registered protocol family 20
[    3.412507] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[    3.412510] pnp: 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    3.412513] pnp: 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    3.412516] pnp: 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    3.414581] Time: tsc clocksource has been installed.
[    3.442761] PCI: Bridge: 0000:00:01.0
[    3.442763]   IO window: 3000-3fff
[    3.442767]   MEM window: c0100000-c01fffff
[    3.442770]   PREFETCH window: e0000000-e7ffffff
[    3.442778] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[    3.442780]   IO window: 00004000-000040ff
[    3.442784]   IO window: 00004400-000044ff
[    3.442788]   PREFETCH window: e8000000-ebffffff
[    3.442792]   MEM window: c4000000-c7ffffff
[    3.442796] PCI: Bus 7, cardbus bridge: 0000:02:00.1
[    3.442798]   IO window: 00004800-000048ff
[    3.442802]   IO window: 00004c00-00004cff
[    3.442806]   PREFETCH window: ec000000-efffffff
[    3.442810]   MEM window: c8000000-cbffffff
[    3.442814] PCI: Bridge: 0000:00:1e.0
[    3.442817]   IO window: 4000-8fff
[    3.442822]   MEM window: c0200000-cfffffff
[    3.442826]   PREFETCH window: e8000000-efffffff
[    3.442840] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    3.443183] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    3.443186] PCI: setting IRQ 11 as level-triggered
[    3.443189] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.443516] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    3.443519] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    3.443533] NET: Registered protocol family 2
[    3.482584] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    3.482673] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    3.484428] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    3.485145] TCP: Hash tables configured (established 131072 bind 65536)
[    3.485149] TCP reno registered
[    3.494731] checking if image is initramfs... it is
[    3.946367] Switched to high resolution mode on CPU 0
[    4.171008] Freeing initrd memory: 7026k freed
[    4.171198] Simple Boot Flag at 0x35 set to 0x1
[    4.171431] audit: initializing netlink socket (disabled)
[    4.171450] audit(1237419079.996:1): initialized
[    4.171537] highmem bounce pool size: 64 pages
[    4.173329] VFS: Disk quotas dquot_6.5.1
[    4.173380] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    4.173487] io scheduler noop registered
[    4.173489] io scheduler anticipatory registered
[    4.173491] io scheduler deadline registered
[    4.173506] io scheduler cfq registered (default)
[    4.173581] Boot video device is 0000:01:00.0
[    4.173745] isapnp: Scanning for PnP cards...
[    4.526635] isapnp: No Plug & Play device found
[    4.550999] Real Time Clock Driver v1.12ac
[    4.551122] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    4.552171] pnp: Device 00:0a activated.
[    4.552319] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    4.552522] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    4.552531] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    4.553047] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    4.553254] input: Macintosh mouse button emulation as /class/input/input0
[    4.553336] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    4.561400] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.561406] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.561552] mice: PS/2 mouse device common for all mice
[    4.561644] EISA: Probing bus 0 at eisa.0
[    4.561652] Cannot allocate resource for EISA slot 1
[    4.561655] Cannot allocate resource for EISA slot 2
[    4.561657] Cannot allocate resource for EISA slot 3
[    4.561659] Cannot allocate resource for EISA slot 4
[    4.561662] Cannot allocate resource for EISA slot 5
[    4.561664] Cannot allocate resource for EISA slot 6
[    4.561666] Cannot allocate resource for EISA slot 7
[    4.561668] Cannot allocate resource for EISA slot 8
[    4.561670] EISA: Detected 0 cards.
[    4.561776] TCP cubic registered
[    4.561792] NET: Registered protocol family 1
[    4.561818] Using IPI No-Shortcut mode
[    4.562007]   Magic number: 1:253:555
[    4.562076]   hash matches device ptya1
[    4.562161]   hash matches device PNP0C0F:06
[    4.562452] Freeing unused kernel memory: 364k freed
[    4.606033] input: AT Translated Set 2 keyboard as /class/input/input1
[    5.755236] fuse init (API version 7.8)
[    5.759821] Capability LSM initialized
[    5.769464] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    5.769470] ACPI: Processor [CPU] (supports 8 throttling states)
[    5.770974] ACPI: Thermal Zone [THM0] (54 C)
[    6.167911] usbcore: registered new interface driver usbfs
[    6.167936] usbcore: registered new interface driver hub
[    6.167955] usbcore: registered new device driver usb
[    6.168729] USB Universal Host Controller Interface driver v3.0
[    6.168803] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    6.168815] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    6.168819] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    6.169018] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    6.169042] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    6.169152] usb usb1: configuration #1 chosen from 1 choice
[    6.169219] hub 1-0:1.0: USB hub found
[    6.169225] hub 1-0:1.0: 2 ports detected
[    6.263445] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[    6.263450] Copyright (c) 1999-2006 Intel Corporation.
[    6.273668] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    6.273673] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    6.273685] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    6.273690] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    6.273715] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    6.273739] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    6.273837] usb usb2: configuration #1 chosen from 1 choice
[    6.273866] hub 2-0:1.0: USB hub found
[    6.273873] hub 2-0:1.0: 2 ports detected
[    6.364025] SCSI subsystem initialized
[    6.369173] libata version 2.21 loaded.
[    6.377590] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    6.377594] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    6.377606] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    6.377610] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    6.377635] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    6.377658] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[    6.377757] usb usb3: configuration #1 chosen from 1 choice
[    6.377783] hub 3-0:1.0: USB hub found
[    6.377789] hub 3-0:1.0: 2 ports detected
[    6.473027] Floppy drive(s): fd0 is 1.44M
[    6.483360] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    6.483365] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[    6.483377] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    6.483381] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    6.483407] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    6.483444] ehci_hcd 0000:00:1d.7: debug port 1
[    6.483450] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    6.483457] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    6.487336] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.487415] usb usb4: configuration #1 chosen from 1 choice
[    6.487446] hub 4-0:1.0: USB hub found
[    6.487452] hub 4-0:1.0: 6 ports detected
[    6.519317] FDC 0 is a National Semiconductor PC87306
[    6.589675] ata_piix 0000:00:1f.1: version 2.11
[    6.589691] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    6.589701] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    6.589740] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    6.589829] scsi0 : ata_piix
[    6.589865] scsi1 : ata_piix
[    6.590302] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
[    6.590306] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
[    3.688000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.692000] Time: acpi_pm clocksource has been installed.
[    3.836000] ata1.00: ATA-6: ST980815A, 3.ALD, max UDMA/100
[    3.836000] ata1.00: 156301488 sectors, multi 16: LBA48 
[    3.852000] ata1.00: configured for UDMA/100
[    4.212000] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R9012, 1121, max UDMA/33
[    4.400000] ata2.00: configured for UDMA/33
[    4.400000] scsi 0:0:0:0: Direct-Access     ATA      ST980815A        3.AL PQ: 0 ANSI: 5
[    4.404000] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R9012 1121 PQ: 0 ANSI: 5
[    4.408000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.420000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.420000] sd 0:0:0:0: [sda] Write Protect is off
[    4.420000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.420000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.420000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.420000] sd 0:0:0:0: [sda] Write Protect is off
[    4.420000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.420000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.420000]  sda:<6>e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:25:12:ad:0d
[    4.660000]  sda1 sda2 sda4
[    4.680000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.696000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    4.716000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    4.728000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.728000] Uniform CD-ROM driver Revision: 3.20
[    4.728000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.732000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.732000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.892000] usb 2-1: configuration #1 chosen from 1 choice
[    5.132000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[    5.316000] usb 2-2: configuration #1 chosen from 1 choice
[    5.320000] hub 2-2:1.0: USB hub found
[    5.320000] hub 2-2:1.0: 3 ports detected
[    5.636000] usb 2-2.2: new full speed USB device using uhci_hcd and address 4
[    5.788000] usb 2-2.2: configuration #1 chosen from 1 choice
[    5.996000] usb 2-2.3: new full speed USB device using uhci_hcd and address 5
[    6.148000] usb 2-2.3: configuration #1 chosen from 1 choice
[    6.156000] usbcore: registered new interface driver hiddev
[    6.168000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[    6.168000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
[    6.176000] input: Logitech Logitech BT Mini-Receiver as /class/input/input3
[    6.176000] input: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.1-2.2
[    6.184000] input: Logitech Logitech BT Mini-Receiver as /class/input/input4
[    6.184000] input,hiddev96: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.1-2.3
[    6.184000] usbcore: registered new interface driver usbhid
[    6.184000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   10.216000] kjournald starting.  Commit interval 5 seconds
[   10.216000] EXT3-fs: mounted filesystem with ordered data mode.
[   26.184000] Linux agpgart interface v0.102 (c) Dave Jones
[   26.204000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.208000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.272000] agpgart: Detected an Intel 855PM Chipset.
[   26.288000] agpgart: AGP aperture is 256M @ 0xd0000000
[   27.168000] iTCO_vendor_support: vendor-support=0
[   27.344000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   27.344000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   27.344000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   27.424000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0552]
[   27.424000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   27.424000] Yenta: Routing CardBus interrupts to PCI
[   27.424000] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21b22, devctl 0x64
[   27.476000] ath_hal: module license 'Proprietary' taints kernel.
[   27.480000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   27.592000] wlan: 0.9.4
[   27.656000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   27.656000] Socket status: 30000086
[   27.656000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   27.656000] cs: IO port probe 0x4000-0x8fff: clean.
[   27.656000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   27.656000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   27.656000] Yenta: CardBus bridge found at 0000:02:00.1 [1014:0552]
[   27.656000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   27.656000] Yenta: Routing CardBus interrupts to PCI
[   27.656000] Yenta TI: socket 0000:02:00.1, mfunc 0x01d21b22, devctl 0x64
[   27.676000] input: PC Speaker as /class/input/input5
[   27.776000] ath_pci: 0.9.4
[   27.828000] intel_rng: FWH not detected
[   27.888000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   27.888000] Socket status: 30000086
[   27.888000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   27.888000] cs: IO port probe 0x4000-0x8fff: clean.
[   27.888000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   27.888000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   27.888000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   28.264000] irda_init()
[   28.264000] NET: Registered protocol family 23
[   28.304000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[   28.304000] serio: Synaptics pass-through port at isa0060/serio1/input0
[   28.324000] ath_rate_sample: 1.2 (0.9.4)
[   28.324000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   28.324000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   28.324000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   28.324000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   28.324000] wifi0: mac 5.6 phy 4.1 5 GHz radio 1.7 2 GHz radio 2.3
[   28.324000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   28.324000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   28.324000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   28.324000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   28.324000] wifi0: Use hw queue 8 for CAB traffic
[   28.324000] wifi0: Use hw queue 9 for beacons
[   28.344000] input: SynPS/2 Synaptics TouchPad as /class/input/input6
[   28.348000] parport_pc 00:0b: reported by Plug and Play ACPI
[   28.348000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   28.388000] wifi0: Atheros 5212: mem=0xc0210000, irq=11
[   28.496000] pnp: Device 00:0c activated.
[   28.496000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   28.496000] nsc-ircc, chip->init
[   28.496000] nsc-ircc, Found chip at base=0x02e
[   28.496000] nsc-ircc, driver loaded (Dag Brattli)
[   28.496000] IrDA: Registered device irda0
[   28.496000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   28.924000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   28.924000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   29.012000] cs: IO port probe 0x100-0x3af: clean.
[   29.016000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   29.016000] cs: IO port probe 0x820-0x8ff: clean.
[   29.016000] cs: IO port probe 0xc00-0xcf7: clean.
[   29.016000] cs: IO port probe 0xa00-0xaff: clean.
[   29.016000] cs: IO port probe 0x100-0x3af: clean.
[   29.016000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   29.016000] cs: IO port probe 0x820-0x8ff: clean.
[   29.016000] cs: IO port probe 0xc00-0xcf7: clean.
[   29.020000] cs: IO port probe 0xa00-0xaff: clean.
[   29.852000] intel8x0_measure_ac97_clock: measured 55472 usecs
[   29.852000] intel8x0: clocking to 48000
[   30.652000] lp0: using parport0 (interrupt-driven).
[   30.748000] ACPI: AC Adapter [AC] (on-line)
[   31.064000] EXT3 FS on sda2, internal journal
[   31.724000] AppArmor: Unable to register AppArmor
[   31.884000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.352000] ACPI: ACPI Dock Station Driver 
[   32.368000] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: found ejectable bay
[   32.368000] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: Adding notify handler
[   32.368000] ACPI: Error installing bay notify handler
[   32.368000] ACPI: Bay [\_SB_.PCI0.IDE0.SCND.MSTR] Added
[   32.396000] ACPI: Battery Slot [BAT0] (battery present)
[   32.428000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   32.544000] input: Power Button (FF) as /class/input/input7
[   32.544000] ACPI: Power Button (FF) [PWRF]
[   32.596000] input: Lid Switch as /class/input/input8
[   32.600000] ACPI: Lid Switch [LID]
[   32.652000] input: Sleep Button (CM) as /class/input/input9
[   32.656000] ACPI: Sleep Button (CM) [SLPB]
[   33.708000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   33.708000] PCI: Setting latency timer of device 0000:00:1f.6 to 64
[   33.724000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   33.812000] MC'97 1 converters and GPIO not ready (0xff00)
[   33.956000] input: TPPS/2 IBM TrackPoint as /class/input/input10
[   34.224000] ppdev: user-space parallel port driver
[   34.428000] NET: Registered protocol family 10
[   34.428000] lo: Disabled Privacy Extensions
[   34.680000] IBM machine detected. Enabling interrupts during APM calls.
[   34.680000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   34.680000] apm: overridden by ACPI.
[   35.824000] thinkpad_acpi: ThinkPad ACPI Extras v0.14
[   35.824000] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   35.824000] thinkpad_acpi: ThinkPad EC firmware 1RHT71WW-3.04
[   35.824000] thinkpad_acpi: another device driver is already handling bay events
[   35.824000] thinkpad_acpi: disabling subdriver bay
[   37.024000] Clocksource tsc unstable (delta = -323535675 ns)
[   45.348000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   47.848000] [drm] Initialized drm 1.1.0 20060810
[   47.852000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   47.856000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   48.100000] NET: Registered protocol family 17
[   50.116000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   50.116000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   50.116000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   51.452000] [drm] Setting GART location based on new memory map
[   51.452000] [drm] writeback test succeeded in 2 usecs
[   60.168000] eth0: no IPv6 routers present
[  162.604000] UDF-fs: No VRS found
[  162.640000] ISO 9660 Extensions: Microsoft Joliet Level 3
[  162.880000] ISOFS: changing to secondary root

Thanks for the help

---

