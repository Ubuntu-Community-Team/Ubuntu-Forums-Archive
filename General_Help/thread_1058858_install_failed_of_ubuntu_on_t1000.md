---
title: "install failed of ubuntu on t1000"
date: 2009-02-03
forum: General Help
---

### Post by axisys on 2009-02-03
I am following this link to install ubuntu on t1000

[https://help.ubuntu.com/community/Installation/Sparc](https://help.ubuntu.com/community/Installation/Sparc)

I have tried to use boot img of both intrepid and hardy but both bombs 
out while trying to detect the disks with this error

```

Detecting disks and all other hardware  ..95%..100%
[  194.651164] SUN4V-DTLB: Error at TPC[f7e03aac], tl 1
[  194.652239] SUN4V-DTLB: TPC<0xf7e03ab4>
[  194.656230] SUN4V-DTLB: O7[f7f71a88]
[  194.660227] SUN4V-DTLB: O7<0xf7f71a90>
[  194.664227] SUN4V-DTLB: vaddr[f7d10000] ctx[66d]
pte[98000000000f0610] error[2]
Program terminated
{0} ok

```

If I go to shell before I try to detect the disk, I notice ```
fdisk -l
``` does not give any output

Here is the ```
dmesg
``` during install

```

Ubuntu installer main menu
--------------------------

Choose the next step in the install process:
  1. Choose language    
  2. Configure the keyboard    
  3. Detect network hardware    
  4. Configure the network    
  5. Choose a mirror of the Ubuntu archive    
  6. Download installer components    
  7. Configure the clock    
  8. Detect disks [*]
  9. Configure iSCSI    
 10. Partition disks    
 11. Install the base system    
 12. Set up users and passwords    
 13. Configure the package manager    
 14. Select and install software    
 15. Build LTSP chroot    
 16. Install the SILO boot loader on a hard disk    
 17. Continue without boot loader    
 18. Finish the installation    
 19. Change debconf priority    
 20. Save debug logs    
 21. Execute a shell    
 22. Abort the installation    
Prompt: '?' for help, default=8> 21

Execute a shell
---------------

Interactive shell

After this message, you will be running "ash", a Bourne-shell clone. 

The root file system is a RAM disk. The hard disk file systems are mounted on 
"/target". The editor available to you is nano. It's very small and easy to 
figure out. To get an idea of what Unix utilities are available to you, use the
"help" command.

Use the "exit" command to return to the installation menu.
[Press enter to continue] 



BusyBox v1.10.2 (2008-09-12 08:47:17 UTC) built-in shell (ash)
Enter 'help' for a list of built-in commands.

~ # dmesg 
[    0.000000] PROMLIB: Sun IEEE Boot Prom 'OBP 4.30.0 2008/12/11 12:13'
[    0.000000] PROMLIB: Root node compatible: sun4v
[    0.000000] Linux version 2.6.25-2-sparc64 (buildd@artigas) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu8) ) #1 Tue Sep 30 14:55:44 UTC 2008
[    0.000000] console [earlyprom0] enabled
[    0.000000] ARCH: SUN4V
[    0.000000] Ethernet address: 00:14:4f:47:fd:ce
[    0.000000] Kernel: Using 2 locked TLB entries for main kernel image.
[    0.000000] Remapping the kernel... done.
[    0.000000] [0000000200000000-fffff80009000000] page_structs=262144 node=0 entry=0/0
[    0.000000] [0000000200000000-fffff80009400000] page_structs=262144 node=0 entry=1/0
[    0.000000] [0000000200000000-fffff80009800000] page_structs=262144 node=0 entry=2/0
[    0.000000] [0000000200000000-fffff80009c00000] page_structs=262144 node=0 entry=3/0
[    0.000000] OF stdout device is: /virtual-devices@100/console@1
[    0.000000] PROM: Built device tree with 68128 bytes of memory.
[    0.000000] MDESC: Size is 33008 bytes.
[    0.000000] PLATFORM: banner-name [Sun Fire(TM) T1000]
[    0.000000] PLATFORM: name [SUNW,Sun-Fire-T1000]
[    0.000000] PLATFORM: hostid [8447fdce]
[    0.000000] PLATFORM: serial# [00ab4130]
[    0.000000] PLATFORM: stick-frequency [3b9aca00]
[    0.000000] PLATFORM: mac-address [144f47fdce]
[    0.000000] PLATFORM: watchdog-resolution [1000 ms]
[    0.000000] PLATFORM: watchdog-max-timeout [31536000000 ms]
[    0.000000] PLATFORM: max-cpus [32]
[    0.000000] On node 0 totalpages: 244356
[    0.000000]   Normal zone: 1790 pages used for memmap
[    0.000000]   Normal zone: 0 pages reserved
[    0.000000]   Normal zone: 242566 pages, LIFO batch:15
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Booting Linux...
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 242566
[    0.000000] Kernel command line: debconf/priority=low DEBIAN_FRONTEND=text
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.004000] clocksource: mult[10000] shift[16]
[    0.004000] clockevent: mult[80000000] shift[31]
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console handover: boot [earlyprom0] -> real [tty0]
[    0.004927] Dentry cache hash table entries: 262144 (order: 8, 2097152 bytes)
[    0.010664] Inode-cache hash table entries: 131072 (order: 7, 1048576 bytes)
[    0.084294] Memory: 1928824k available (2808k kernel code, 1200k data, 160k init) [fffff80000000000,000000007fdb8000]
[    0.084414] SLUB: Genslabs=13, HWalign=32, Order=0-2, MinObjects=8, CPUs=1, Nodes=1
[    0.164014] Calibrating delay using timer specific routine.. 1999.16 BogoMIPS (lpj=3998337)
[    0.164149] Security Framework initialized
[    0.164178] SELinux:  Disabled at boot.
[    0.164202] Capability LSM initialized
[    0.164237] Mount-cache hash table entries: 512
[    0.164739] Initializing cgroup subsys ns
[    0.165567] net_namespace: 1000 bytes
[    0.165619] ldc.c:v1.0 (June 25, 2007)
[    0.165633] ldc: Domaining disabled.
[    0.166419] NET: Registered protocol family 16
[    0.178659] VIO: Adding device channel-devices
[    0.178844] VIO: Adding device vldc-port-0-0
[    0.179015] VIO: Adding device vldc-port-0-1
[    0.179185] VIO: Adding device vldc-port-0-2
[    0.179356] VIO: Adding device vldc-port-1-0
[    0.179527] VIO: Adding device vldc-port-3-0
[    0.179714] VIO: Adding device vldc-port-3-8
[    0.179896] VIO: Adding device ds-1
[    0.180090] VIO: Adding device ds-0
[    0.181352] PCI: Probing for controllers.
[    0.181401] SUN4V_PCI: Registered hvapi major[1] minor[0]
[    0.181443] /pci@780: SUN4V PCI Bus Module
[    0.181471] /pci@780: PCI IO[e810000000] MEM[ea00000000]
[    0.227207] /pci@7c0: SUN4V PCI Bus Module
[    0.227241] /pci@7c0: PCI IO[f010000000] MEM[f200000000]
[    0.272879] PCI: Scanning PBM /pci@7c0
[    0.275642] PCI: Scanning PBM /pci@780
[    0.275830] ebus: No EBus's found.
[    0.276204] ds.c:v1.0 (Jul 11, 2007)
[    0.280576] usbcore: registered new interface driver usbfs
[    0.280766] usbcore: registered new interface driver hub
[    0.281000] usbcore: registered new device driver usb
[    0.298091] NET: Registered protocol family 2
[    0.300034] Switched to high resolution mode on CPU 0
[    0.332195] IP route cache hash table entries: 65536 (order: 6, 524288 bytes)
[    0.333352] TCP established hash table entries: 262144 (order: 9, 4194304 bytes)
[    0.348316] TCP bind hash table entries: 65536 (order: 6, 524288 bytes)
[    0.350224] TCP: Hash tables configured (established 262144 bind 65536)
[    0.350256] TCP reno registered
[    0.360572] checking if image is initramfs... it is
[    2.459681] Freeing initrd memory: 5241k freed
[    2.460505] Mini RTC Driver
[    2.461575] audit: initializing netlink socket (disabled)
[    2.461628] type=2000 audit(1233615920.644:1): initialized
[    2.462118] Total HugeTLB memory allocated, 0
[    2.474512] VFS: Disk quotas dquot_6.5.1
[    2.474883] Dquot-cache hash table entries: 1024 (order 0, 8192 bytes)
[    2.475699] io scheduler noop registered
[    2.475728] io scheduler anticipatory registered
[    2.475755] io scheduler deadline registered
[    2.476072] io scheduler cfq registered (default)
[    2.599349] Console: switching to mono PROM 80x34
[    2.811762] [drm] Initialized drm 1.1.0 20060810
[    2.812333] f027a4d0: ttyS0 at I/O 0x0 (irq = 1) is a SUN4V HCONS
[    2.816294] console [ttyHV0] enabled
[    2.824872] f028739c: ttyS0 at MMIO 0xf820c2c000 (irq = 18) is a ST16650V2
[    2.834500] brd: module loaded
[    2.837602] loop: module loaded
[    2.841284] usbcore: registered new interface driver libusual
[    2.844888] mice: PS/2 mouse device common for all mice
[    2.852614] TCP cubic registered
[    2.856451] NET: Registered protocol family 1
[    2.860236] NET: Registered protocol family 17
[    2.864729] registered taskstats version 1
[    4.576613] tg3.c:v3.91 (April 18, 2008)
[    4.613567] eth0: Tigon3 [partno(BCM95714) rev 9001 PHY(5714)] (PCIX:133MHz:64-bit) 10/100/1000Base-T Ethernet 00:14:4f:47:fd:ce
[    4.616309] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    4.620298] eth0: dma_rwctrl[76148000] dma_mask[32-bit]
[    4.624376] PCI: Enabling device: (0001:03:04.1), cmd 2
[    4.663021] eth1: Tigon3 [partno(BCM95714) rev 9001 PHY(5714)] (PCIX:133MHz:64-bit) 10/100/1000Base-T Ethernet 00:14:4f:47:fd:cf
[    4.664304] eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    4.668301] eth1: dma_rwctrl[76148000] dma_mask[32-bit]
[    4.672392] PCI: Enabling device: (0001:04:01.0), cmd 2
[    4.741150] eth2: Tigon3 [partno(BCM95704) rev 2100 PHY(5704)] (PCIX:100MHz:64-bit) 10/100/1000Base-T Ethernet 00:14:4f:47:fd:d0
[    4.744308] eth2: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    4.748307] eth2: dma_rwctrl[769f8000] dma_mask[32-bit]
[    4.752383] PCI: Enabling device: (0001:04:01.1), cmd 2
[    4.817178] eth3: Tigon3 [partno(BCM95704) rev 2100 PHY(5704)] (PCIX:100MHz:64-bit) 10/100/1000Base-T Ethernet 00:14:4f:47:fd:d1
[    4.820313] eth3: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    4.824312] eth3: dma_rwctrl[769f8000] dma_mask[32-bit]
[   12.872242] SCSI subsystem initialized
[   12.890744] Initializing USB Mass Storage driver...
[   12.890815] usbcore: registered new interface driver usb-storage
[   12.890831] USB Mass Storage support registered.
[   20.385275] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   20.385275] tg3: eth0: Flow control is off for TX and off for RX.
~ # fdisk -l
~ # 

```

---

### Post by Twirlcan on 2009-02-03
Just a disclaimer.  I have never worked on Sun hardware that has a SATA drive like this one does...but it appears that your disk is not recognised or there are other problems 

At the OK prompt you need to do either a probe-scsi-all or maybe a probe-ide-all.

I am guessing that the sata drive is seen as a SCSI drive but there is a chance that it might be SATA specific, so see if you can check some documentation.

If it does not work, check the cables, check the drive and make sure everything is seated properly.

Another thing you can do in opfw is check the disk this way:

dev /disk
and then type: .properties

another one you can use to show all devices is show-devs /

This should give you all the devices on the root tree of your opfw directorty.  Look for a disk there.

Sometimes opfw is crap at reading file systems as well so you might want to convert your disk to FAT32 and then probe for it again.

---

### Post by randara on 2009-04-16
I have the same problem, but I get this

```
~# lspci
...
ERROR: HV Abort: Uncorrectable Error in Hyperpriv mode (1e)

```

Any clues?

---

