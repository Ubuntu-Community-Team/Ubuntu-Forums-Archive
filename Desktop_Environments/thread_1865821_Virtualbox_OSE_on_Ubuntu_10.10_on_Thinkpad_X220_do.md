---
title: "Virtualbox OSE on Ubuntu 10.10 on Thinkpad X220 does not work."
date: 2011-10-20
forum: Desktop Environments
---

### Post by pcarlos853 on 2011-10-20
Hello,

I bought a new Thinkpad X220 last week. I installed Ubuntu 10.10 by following [this guide (Link Here)]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.10_%28Maverick_Meerkat%29_on_a_ThinkPad_X220") the guide says

```
the Sandybridge GPU is blacklisted for 3D, Compiz and desktop effects.  The fix for this is more involved. It requires installing an updated X,  Compiz and kernel. Fortunately, Ubuntu's PPAs make this much easier. The  original instructions I followed are [here]("http://phoronix.com/forums/showthread.php?29110-Intel-s-Linux-Sandy-Bridge-Graphics-Still-Troubling&p=168137#post168137")  (you can install both PPAs before doing the upgrade/update), but it  turns out (after consulting Jools Wills, the author of those  instructions and keeper of the PPA) you also need a newer kernel, which I  have got from [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.37-natty/").  You need to download the two i386 files and the all file and install  them using "sudo dpkg -i". That all worked for me without a hitch, which  was very painless. One reboot, and I could enable desktop effects and  my X now appears to be rock solid. 
```So the kernal is now 2.6.37 (from what I understand, I am still new to kernel stuff). I need to run a Windows VM for work, however both Virtualbox (x64) OSE, Oracle, and vmware player do not work. When I try to start a VM I get the following error:

```
 p, li { white-space: pre-wrap; } Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

```When I try to run /etc/init.d/vboxdrv setup I get "bash: /etc/init.d/vboxdrv: No such file or directory" 

Also if I try to run it from a root shell I get:

```
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.37-020637-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.

```

Does anyone know how I could fix this problem? Let me know if you need anymore info.

Thanks!
Carlos

---

### Post by deloquencia on 2011-10-20
Hello,


as far as I know the kernel modules vbox* (vboxdrv, vboxpci, vboxnetadp, vboxnetflt) are compiled when dpkg installs the Oracle package virtualbox. When the dynamic kernel module support (dkms) is not present you've got to recompile the modules every time you change the kernel.

Try following with Oracles VirtualBox, perhaps it fix your issue. When you're trying it with the Open Source Edition (OSE) you have additionaly to install the sourc codes for the kernel modules (virtualbox-ose-dkms and of course the OSE itself virtualbox-ose)


**sudo apt-get install dkms**
**sudo apt-get -reinstall install virtualbox-4.1**

dpkg starts the init script vboxdrv after the installation, so check the loaded modules and the syslog.

**sudo lsmod | grep -e vbox.***
**sudo tail -n 20 /var/log/syslog | grep -e vboxdrv.***

The syslog should say something like that:

[I]Oct 20 21:28:28 deepthroat kernel: [ 5665.127950] vboxdrv: Found 2 processor cores.
Oct 20 21:28:28 deepthroat kernel: [ 5665.128482] vboxdrv: fAsync=0 offMin=0x564 offMax=0x1a78
Oct 20 21:28:28 deepthroat kernel: [ 5665.128625] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Oct 20 21:28:28 deepthroat kernel: [ 5665.128631] vboxdrv: Successfully loaded version 4.1.2 (interface 0x00190000).[/I]

Tell me what syslog tells you? And tell me what apt-get writes to console during the installation of virtualbox and dkms.


I hope I could help you at least a little bit.

---

### Post by pcarlos853 on 2011-10-20
Hi,

Thanks for the quick reply! I have Orcale Virtualbox installed.

I already have dkms installed. The output of the other command is as follows:

[B]sudo apt-get --reinstall install virtualbox-4.1
[sudo] password for carlos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of virtualbox-4.1 is not possible, it cannot be downloaded.[/B]

The syslog should say something like that:
[B]The following packages were automatically installed and are no longer required:
  libpython2.7 python2.7 python2.7-minimal
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.[/B]

**sudo lsmod | grep -e vbox.***
No output 
[B]sudo tail -n 20 /var/log/syslog | grep -e vboxdrv.*
[/B]No output


Any other ideas? 

Thanks!
Carlos

---

### Post by deloquencia on 2011-10-20
Sorry, it looks like virtualbox is not installed properly at your system. Re-install it with the package provided by Oracle at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) and then go ahead.

Don't worry about the AMD64 packages it seems it's for both CPUs... "if you are running a 64-bit kernel, install the appropriate AMD64 package (it does not matter if you have an Intel or an AMD CPU)"

---

### Post by sieve on 2011-10-20
I've had success in uninstalling and reinstalling Virtualbox.  Kind-of a pain, but not so bad if you keep the various machine files backed up.

---

### Post by pcarlos853 on 2011-10-20
I have already reinstalled virtualbox a few times. Anyway I did it again. I installed the version for Ubuntu 10.10 x64. I am still getting the same errors unfortunately (I attached a screenshot).

Any other ideas?

Thanks a bunch!
Carlos

---

### Post by deloquencia on 2011-10-21
That's odd... 

So still your missing the modules and perhaps also the script vboxdrv in /etc/init.d... just like you wrote before "When I try to run /etc/init.d/vboxdrv setup I get "bash: /etc/init.d/vboxdrv: No such file or directory"

How you've installed virtualbox? Which package you've chose? The Debian package for your Ubuntu flavor - 
Ubuntu 10.10 ("Maverick Meerkat") or the generic Package for all distributions, which in fact is a script which installs the package? When you've chose the last option, where did you installed it in /usr, in /opt or in /usr/local or somewhere, where I even can't imagine of ;)

It looks like your installation is still not working, but lets go further. I tried without and traced your problem and got the same one. 

I checked the package virtualbox 4.1.4 at oracle ([http://download.virtualbox.org/virtualbox/4.1.4/virtualbox-4.1_4.1.4-74291~Ubuntu~maverick_amd64.deb](http://download.virtualbox.org/virtualbox/4.1.4/virtualbox-4.1_4.1.4-74291~Ubuntu~maverick_amd64.deb)) and the script vboxdrv **is** in the package.

Try to run it again?

**sudo /etc/init.d/vboxdrv start**

When still it's no-go - so let's try to load the modules manualy, which worked at my setup. Four modules are needed, vboxpci, vboxnetadp, vboxnetflt and vboxdrv.

[B]sudo modprobe -v vboxpci
sudo modprobe -v vboxnetadp
sudo modprobe -v vboxnetflt
sudo modprobe -v vboxdrv[/B]

The last thing which came to my mind: Are you a member of the group vboxusers? You've got to be a member to access all devices in /dev/ which virtualbox works with. Check with...

**groups**

When your not a member so run:

**sudo gpasswd --add carlos vboxusers**

carlos is your username, as far as I saw from your screenshot. But with this missing the error messages from virtualbox would be just different, but please check it if you belong to this group.

Hope it helped a little bit...
Thomas

---

### Post by pcarlos853 on 2011-10-22
Thanks for the reply!

So I ran vboxdrv start and I got output (below). The last time I ran it I had installed Virtual box for all distributions for troubleshooting. 
[B]
carlos@X200:~$ sudo /etc/init.d/vboxdrv start
[sudo] password for carlos: 
 * Starting VirtualBox kernel modules                                           
 * modprobe vboxdrv failed. Please use 'dmesg' to find out why
[/B]
When I type dmesg I get (also attached as a txt for easier viewing):

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.37-020637-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #201101050908 SMP Wed Jan 5 09:09:44 UTC 2011
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637-generic root=UUID=15f3a1c7-5d7d-463c-a74f-b32754f2442e ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000da99f000 (usable)
[    0.000000]  BIOS-e820: 00000000da99f000 - 00000000dae9f000 (reserved)
[    0.000000]  BIOS-e820: 00000000dae9f000 - 00000000daf9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000daf9f000 - 00000000dafff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dafff000 - 00000000db000000 (usable)
[    0.000000]  BIOS-e820: 00000000db000000 - 00000000dfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed08000 - 00000000fed09000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffd20000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000011e600000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: 4286CTO/4286CTO, BIOS 8DET51WW (1.21 ) 08/02/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x11e600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0C0000000 mask FE0000000 write-back
[    0.000000]   4 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   5 base 0DB000000 mask FFF000000 uncachable
[    0.000000]   6 base 100000000 mask FE0000000 write-back
[    0.000000]   7 base 11F000000 mask FFF000000 uncachable
[    0.000000]   8 base 11E800000 mask FFF800000 uncachable
[    0.000000]   9 base 11E600000 mask FFFE00000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xdb000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000db000000
[    0.000000]  0000000000 - 00db000000 page 2M
[    0.000000] kernel direct mapping tables up to db000000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000011e600000
[    0.000000]  0100000000 - 011e600000 page 2M
[    0.000000] kernel direct mapping tables up to 11e600000 @ da999000-da99f000
[    0.000000] RAMDISK: 16fa4000 - 18040000
[    0.000000] ACPI: RSDP 00000000000f00e0 00024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 00000000daffe120 000A4 (v01 LENOVO TP-8D    00001210 PTEC 00000002)
[    0.000000] ACPI: FACP 00000000dafe7000 000F4 (v04 LENOVO TP-8D    00001210 PTL  00000002)
[    0.000000] ACPI: DSDT 00000000dafea000 0F643 (v01 LENOVO TP-8D    00001210 INTL 20061109)
[    0.000000] ACPI: FACS 00000000daf2d000 00040
[    0.000000] ACPI: SLIC 00000000daffd000 00176 (v01 LENOVO TP-8D    00001210 PTEC 00000001)
[    0.000000] ACPI: SSDT 00000000daffc000 00249 (v01 LENOVO TP-SSDT2 00000200 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000daffb000 00033 (v01 LENOVO TP-SSDT1 00000100 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000daffa000 007A7 (v01 LENOVO SataAhci 00001000 INTL 20061109)
[    0.000000] ACPI: HPET 00000000dafe6000 00038 (v01 LENOVO TP-8D    00001210 PTL  00000002)
[    0.000000] ACPI: APIC 00000000dafe5000 00098 (v01 LENOVO TP-8D    00001210 PTL  00000002)
[    0.000000] ACPI: MCFG 00000000dafe4000 0003C (v01 LENOVO TP-8D    00001210 PTL  00000002)
[    0.000000] ACPI: ECDT 00000000dafe3000 00052 (v01 LENOVO TP-8D    00001210 PTL  00000002)
[    0.000000] ACPI: ASF! 00000000dafe9000 000A5 (v32 LENOVO TP-8D    00001210 PTL  00000002)
[    0.000000] ACPI: TCPA 00000000dafe2000 00032 (v02    PTL   LENOVO 06040000 LNVO 00000001)
[    0.000000] ACPI: SSDT 00000000dafe1000 00AAB (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000dafe0000 00996 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: UEFI 00000000dafdf000 0003E (v01 LENOVO TP-8D    00001210 PTL  00000002)
[    0.000000] ACPI: UEFI 00000000dafde000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000dafdd000 00292 (v01 LENOVO TP-8D    00001210 PTL  00000002)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000011e600000
[    0.000000] Initmem setup node 0 0000000000000000-000000011e600000
[    0.000000]   NODE_DATA [000000011e5fb000 - 000000011e5fffff]
[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff88011a400000-ffff88011ddfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0011e600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000da99f
[    0.000000]     0: 0x000dafff -> 0x000db000
[    0.000000]     0: 0x00100000 -> 0x0011e600
[    0.000000] On node 0 totalpages: 1018669
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3919 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 875992 pages, LIFO batch:31
[    0.000000]   Normal zone: 1701 pages used for memmap
[    0.000000]   Normal zone: 122715 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
[    0.000000] PM: Registered nosave memory: 00000000da99f000 - 00000000dae9f000
[    0.000000] PM: Registered nosave memory: 00000000dae9f000 - 00000000daf9f000
[    0.000000] PM: Registered nosave memory: 00000000daf9f000 - 00000000dafff000
[    0.000000] PM: Registered nosave memory: 00000000db000000 - 00000000dfa00000
[    0.000000] PM: Registered nosave memory: 00000000dfa00000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed08000
[    0.000000] PM: Registered nosave memory: 00000000fed08000 - 00000000fed09000
[    0.000000] PM: Registered nosave memory: 00000000fed09000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffd20000
[    0.000000] PM: Registered nosave memory: 00000000ffd20000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at dfa00000 (gap: dfa00000:18600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88001fc00000 s83520 r8192 d22976 u262144
[    0.000000] pcpu-alloc: s83520 r8192 d22976 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1002626
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637-generic root=UUID=15f3a1c7-5d7d-463c-a74f-b32754f2442e ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3918036k/4691968k available (5838k kernel code, 617292k absent, 156640k reserved, 5079k data, 1012k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2791.360 MHz processor.
[    0.000015] Calibrating delay loop (skipped), value calculated using timer frequency.. 5582.72 BogoMIPS (lpj=27913600)
[    0.000024] pid_max: default: 32768 minimum: 301
[    0.000075] Security Framework initialized
[    0.000115] AppArmor: AppArmor initialized
[    0.001279] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003896] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004915] Mount-cache hash table entries: 256
[    0.005165] Initializing cgroup subsys ns
[    0.005172] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.005178] Initializing cgroup subsys cpuacct
[    0.005188] Initializing cgroup subsys memory
[    0.005205] Initializing cgroup subsys devices
[    0.005209] Initializing cgroup subsys freezer
[    0.005213] Initializing cgroup subsys net_cls
[    0.005278] CPU: Physical Processor ID: 0
[    0.005282] CPU: Processor Core ID: 0
[    0.005296] mce: CPU supports 7 MCE banks
[    0.005326] CPU0: Thermal monitoring enabled (TM1)
[    0.005345] using mwait in idle threads.
[    0.005349] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
[    0.005363] ... version:                3
[    0.005366] ... bit width:              48
[    0.005370] ... generic registers:      4
[    0.005373] ... value mask:             0000ffffffffffff
[    0.005377] ... max period:             000000007fffffff
[    0.005381] ... fixed-purpose events:   3
[    0.005384] ... event mask:             000000070000000f
[    0.012778] ACPI: Core revision 20101013
[    0.061590] ftrace: allocating 27663 entries in 109 pages
[    0.094108] Not enabling x2apic, Intr-remapping init failed.
[    0.094115] Setting APIC routing to flat
[    0.094514] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.194310] CPU0: Intel(R) Core(TM) i7-2640M CPU @ 2.80GHz stepping 07
[    0.305817] Booting Node   0, Processors  #1 #2 #3
[    0.844267] Brought up 4 CPUs
[    0.844275] Total of 4 processors activated (22328.51 BogoMIPS).
[    0.850376] devtmpfs: initialized
[    0.852691] regulator: core version 0.5
[    0.852775] regulator: dummy: 
[    0.852806] Time: 21:39:36  Date: 10/22/11
[    0.852883] NET: Registered protocol family 16
[    0.853114] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.853120] ACPI: bus type pci registered
[    0.853619] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.853626] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.870534] PCI: Using configuration type 1 for base access
[    0.872203] bio: create slab <bio-0> at 0
[    0.877461] ACPI: EC: EC description table is found, configuring boot EC
[    0.897008] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.016119] ACPI: SSDT 00000000dae8c018 008C0 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    1.017407] ACPI: Dynamic OEM Table Load:
[    1.017414] ACPI: SSDT           (null) 008C0 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    1.054566] ACPI: SSDT 00000000dae8da98 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    1.055946] ACPI: Dynamic OEM Table Load:
[    1.055952] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    1.103832] ACPI: SSDT 00000000dae8bd98 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    1.105095] ACPI: Dynamic OEM Table Load:
[    1.105102] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    1.155421] ACPI: Interpreter enabled
[    1.155428] ACPI: (supports S0 S3 S4 S5)
[    1.155484] ACPI: Using IOAPIC for interrupt routing
[    1.204735] ACPI Exception: AE_NOT_FOUND, Evaluating _PRW (20101013/scan-723)
[    1.207228] ACPI Exception: AE_NOT_FOUND, Evaluating _PRW (20101013/scan-723)
[    1.209772] ACPI Exception: AE_NOT_FOUND, Evaluating _PRW (20101013/scan-723)
[    1.210851] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    1.211098] ACPI: Power Resource [PUBS] (on)
[    1.214186] ACPI: ACPI Dock Station Driver: 3 docks/bays found
[    1.214195] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.214635] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.214791] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.214797] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.214803] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.214810] pci_root PNP0A08:00: host bridge window [mem 0xdfa00000-0xfebfffff]
[    1.214815] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed4bfff]
[    1.214844] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    1.214932] pci 0000:00:02.0: [8086:0126] type 0 class 0x000300
[    1.214961] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf03fffff 64bit]
[    1.214979] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    1.214992] pci 0000:00:02.0: reg 20: [io  0x5000-0x503f]
[    1.215119] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    1.215170] pci 0000:00:16.0: reg 10: [mem 0xf2625000-0xf262500f 64bit]
[    1.215301] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.215311] pci 0000:00:16.0: PME# disabled
[    1.215360] pci 0000:00:16.3: [8086:1c3d] type 0 class 0x000700
[    1.215401] pci 0000:00:16.3: reg 10: [io  0x50b0-0x50b7]
[    1.215422] pci 0000:00:16.3: reg 14: [mem 0xf262c000-0xf262cfff]
[    1.215608] pci 0000:00:19.0: [8086:1502] type 0 class 0x000200
[    1.215652] pci 0000:00:19.0: reg 10: [mem 0xf2600000-0xf261ffff]
[    1.215674] pci 0000:00:19.0: reg 14: [mem 0xf262b000-0xf262bfff]
[    1.215695] pci 0000:00:19.0: reg 18: [io  0x5080-0x509f]
[    1.215818] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    1.215827] pci 0000:00:19.0: PME# disabled
[    1.215880] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    1.215924] pci 0000:00:1a.0: reg 10: [mem 0xf262a000-0xf262a3ff]
[    1.216079] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.216088] pci 0000:00:1a.0: PME# disabled
[    1.216144] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    1.216182] pci 0000:00:1b.0: reg 10: [mem 0xf2620000-0xf2623fff 64bit]
[    1.216318] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.216327] pci 0000:00:1b.0: PME# disabled
[    1.216375] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    1.216523] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.216533] pci 0000:00:1c.0: PME# disabled
[    1.216586] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    1.216736] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.216746] pci 0000:00:1c.1: PME# disabled
[    1.216800] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
[    1.216949] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.216958] pci 0000:00:1c.3: PME# disabled
[    1.217009] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
[    1.217150] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.217158] pci 0000:00:1c.4: PME# disabled
[    1.217211] pci 0000:00:1c.6: [8086:1c1c] type 1 class 0x000604
[    1.217351] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    1.217360] pci 0000:00:1c.6: PME# disabled
[    1.217421] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    1.217466] pci 0000:00:1d.0: reg 10: [mem 0xf2629000-0xf26293ff]
[    1.217623] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.217632] pci 0000:00:1d.0: PME# disabled
[    1.217679] pci 0000:00:1f.0: [8086:1c4f] type 0 class 0x000601
[    1.217906] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    1.217956] pci 0000:00:1f.2: reg 10: [io  0x50a8-0x50af]
[    1.217978] pci 0000:00:1f.2: reg 14: [io  0x50bc-0x50bf]
[    1.217999] pci 0000:00:1f.2: reg 18: [io  0x50a0-0x50a7]
[    1.218020] pci 0000:00:1f.2: reg 1c: [io  0x50b8-0x50bb]
[    1.218041] pci 0000:00:1f.2: reg 20: [io  0x5060-0x507f]
[    1.218063] pci 0000:00:1f.2: reg 24: [mem 0xf2628000-0xf26287ff]
[    1.218151] pci 0000:00:1f.2: PME# supported from D3hot
[    1.218159] pci 0000:00:1f.2: PME# disabled
[    1.218201] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    1.218240] pci 0000:00:1f.3: reg 10: [mem 0xf2624000-0xf26240ff 64bit]
[    1.218294] pci 0000:00:1f.3: reg 20: [io  0xefa0-0xefbf]
[    1.218465] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.218475] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.218486] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.218501] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.218878] pci 0000:03:00.0: [8086:0085] type 0 class 0x000280
[    1.219239] pci 0000:03:00.0: reg 10: [mem 0xf2500000-0xf2501fff 64bit]
[    1.220666] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    1.220722] pci 0000:03:00.0: PME# disabled
[    1.220997] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    1.221007] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    1.221017] pci 0000:00:1c.1:   bridge window [mem 0xf2500000-0xf25fffff]
[    1.221033] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.221138] pci 0000:00:1c.3: PCI bridge to [bus 05-0c]
[    1.221148] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    1.221157] pci 0000:00:1c.3:   bridge window [mem 0xf1d00000-0xf24fffff]
[    1.221173] pci 0000:00:1c.3:   bridge window [mem 0xf0400000-0xf0bfffff 64bit pref]
[    1.221375] pci 0000:0d:00.0: [1180:e823] type 0 class 0x000880
[    1.221412] pci 0000:0d:00.0: reg 10: [mem 0xf1500000-0xf15000ff]
[    1.221655] pci 0000:0d:00.0: supports D1 D2
[    1.221659] pci 0000:0d:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.221714] pci 0000:0d:00.0: PME# disabled
[    1.221780] pci 0000:00:1c.4: PCI bridge to [bus 0d-0d]
[    1.221789] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    1.221799] pci 0000:00:1c.4:   bridge window [mem 0xf1500000-0xf1cfffff]
[    1.221813] pci 0000:00:1c.4:   bridge window [mem 0xf0c00000-0xf13fffff 64bit pref]
[    1.221953] pci 0000:0e:00.0: [1033:0194] type 0 class 0x000c03
[    1.221999] pci 0000:0e:00.0: reg 10: [mem 0xf1400000-0xf1401fff 64bit]
[    1.222182] pci 0000:0e:00.0: PME# supported from D0 D3hot D3cold
[    1.222192] pci 0000:0e:00.0: PME# disabled
[    1.222240] pci 0000:00:1c.6: PCI bridge to [bus 0e-0e]
[    1.222249] pci 0000:00:1c.6:   bridge window [io  0xf000-0x0000] (disabled)
[    1.222259] pci 0000:00:1c.6:   bridge window [mem 0xf1400000-0xf14fffff]
[    1.222274] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.222335] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.222590] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    1.222668] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    1.222744] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    1.222829] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    1.222915] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP7._PRT]
[    1.230278] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    1.230477] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 9 10 11)
[    1.230668] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 9 10 11)
[    1.230855] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    1.231050] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11)
[    1.231208] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    1.231398] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    1.231585] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11)
[    1.231673] HEST: Table is not found!
[    1.231795] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.231818] vgaarb: loaded
[    1.232168] SCSI subsystem initialized
[    1.232268] libata version 3.00 loaded.
[    1.232356] usbcore: registered new interface driver usbfs
[    1.232378] usbcore: registered new interface driver hub
[    1.232434] usbcore: registered new device driver usb
[    1.233258] wmi: Skipping duplicate GUID 05901221-D566-11D1-B2F0-00A0C9062910
[    1.233276] wmi: Mapper loaded
[    1.233279] PCI: Using ACPI for IRQ routing
[    1.233284] PCI: pci_cache_line_size set to 64 bytes
[    1.233788] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    1.233794] reserve RAM buffer: 00000000da99f000 - 00000000dbffffff 
[    1.233801] reserve RAM buffer: 00000000db000000 - 00000000dbffffff 
[    1.233806] reserve RAM buffer: 000000011e600000 - 000000011fffffff 
[    1.233992] NetLabel: Initializing
[    1.233996] NetLabel:  domain hash size = 128
[    1.233999] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.234029] NetLabel:  unlabeled traffic allowed by default
[    1.234106] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.234121] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.236151] Switching to clocksource tsc
[    1.249722] AppArmor: AppArmor Filesystem Enabled
[    1.249753] pnp: PnP ACPI init
[    1.249790] ACPI: bus type pnp registered
[    1.251058] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    1.251064] pnp 00:00: [mem 0x000c0000-0x000c3fff]
[    1.251069] pnp 00:00: [mem 0x000c4000-0x000c7fff]
[    1.251073] pnp 00:00: [mem 0x000c8000-0x000cbfff]
[    1.251083] pnp 00:00: [mem 0x000cc000-0x000cffff]
[    1.251087] pnp 00:00: [mem 0x000d0000-0x000d3fff]
[    1.251092] pnp 00:00: [mem 0x000d4000-0x000d7fff]
[    1.251096] pnp 00:00: [mem 0x000d8000-0x000dbfff]
[    1.251101] pnp 00:00: [mem 0x000dc000-0x000dffff]
[    1.251105] pnp 00:00: [mem 0x000e0000-0x000e3fff]
[    1.251110] pnp 00:00: [mem 0x000e4000-0x000e7fff]
[    1.251114] pnp 00:00: [mem 0x000e8000-0x000ebfff]
[    1.251119] pnp 00:00: [mem 0x000ec000-0x000effff]
[    1.251123] pnp 00:00: [mem 0x000f0000-0x000fffff]
[    1.251128] pnp 00:00: [mem 0x00100000-0xdf9fffff]
[    1.251132] pnp 00:00: [mem 0xfec00000-0xfed3ffff]
[    1.251137] pnp 00:00: [mem 0xfed4c000-0xffffffff]
[    1.251297] pnp 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.251353] pnp 00:01: [bus 00-fe]
[    1.251358] pnp 00:01: [io  0x0cf8-0x0cff]
[    1.251363] pnp 00:01: [io  0x0000-0x0cf7 window]
[    1.251368] pnp 00:01: [io  0x0d00-0xffff window]
[    1.251373] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    1.251379] pnp 00:01: [mem 0x000c0000-0x000c3fff window]
[    1.251384] pnp 00:01: [mem 0x000c4000-0x000c7fff window]
[    1.251388] pnp 00:01: [mem 0x000c8000-0x000cbfff window]
[    1.251393] pnp 00:01: [mem 0x000cc000-0x000cffff window]
[    1.251398] pnp 00:01: [mem 0x000d0000-0x000d3fff window]
[    1.251403] pnp 00:01: [mem 0x000d4000-0x000d7fff window]
[    1.251408] pnp 00:01: [mem 0x000d8000-0x000dbfff window]
[    1.251413] pnp 00:01: [mem 0x000dc000-0x000dffff window]
[    1.251418] pnp 00:01: [mem 0x000e0000-0x000e3fff window]
[    1.251423] pnp 00:01: [mem 0x000e4000-0x000e7fff window]
[    1.251428] pnp 00:01: [mem 0x000e8000-0x000ebfff window]
[    1.251433] pnp 00:01: [mem 0x000ec000-0x000effff window]
[    1.251438] pnp 00:01: [mem 0xdfa00000-0xfebfffff window]
[    1.251443] pnp 00:01: [mem 0xfed40000-0xfed4bfff window]
[    1.251571] pnp 00:01: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.251751] pnp 00:02: [io  0x0010-0x001f]
[    1.251756] pnp 00:02: [io  0x0090-0x009f]
[    1.251760] pnp 00:02: [io  0x0024-0x0025]
[    1.251764] pnp 00:02: [io  0x0028-0x0029]
[    1.251768] pnp 00:02: [io  0x002c-0x002d]
[    1.251773] pnp 00:02: [io  0x0030-0x0031]
[    1.251777] pnp 00:02: [io  0x0034-0x0035]
[    1.251781] pnp 00:02: [io  0x0038-0x0039]
[    1.251785] pnp 00:02: [io  0x003c-0x003d]
[    1.251789] pnp 00:02: [io  0x00a4-0x00a5]
[    1.251798] pnp 00:02: [io  0x00a8-0x00a9]
[    1.251802] pnp 00:02: [io  0x00ac-0x00ad]
[    1.251806] pnp 00:02: [io  0x00b0-0x00b5]
[    1.251810] pnp 00:02: [io  0x00b8-0x00b9]
[    1.251815] pnp 00:02: [io  0x00bc-0x00bd]
[    1.251819] pnp 00:02: [io  0x0050-0x0053]
[    1.251823] pnp 00:02: [io  0x0072-0x0077]
[    1.251827] pnp 00:02: [io  0x0400-0x047f]
[    1.251832] pnp 00:02: [io  0x0500-0x057f]
[    1.251836] pnp 00:02: [io  0x0800-0x080f]
[    1.251840] pnp 00:02: [io  0x15e0-0x15ef]
[    1.251845] pnp 00:02: [io  0x1600-0x167f]
[    1.251849] pnp 00:02: [mem 0xf8000000-0xfbffffff]
[    1.251854] pnp 00:02: [mem 0x00000000-0x00000fff]
[    1.251858] pnp 00:02: [mem 0xfed1c000-0xfed1ffff]
[    1.251863] pnp 00:02: [mem 0xfed10000-0xfed13fff]
[    1.251867] pnp 00:02: [mem 0xfed18000-0xfed18fff]
[    1.251872] pnp 00:02: [mem 0xfed19000-0xfed19fff]
[    1.251876] pnp 00:02: [mem 0xfed45000-0xfed4bfff]
[    1.252058] pnp 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.252195] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.252264] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.252286] pnp 00:04: [io  0x0000-0x000f]
[    1.252291] pnp 00:04: [io  0x0080-0x008f]
[    1.252295] pnp 00:04: [io  0x00c0-0x00df]
[    1.252300] pnp 00:04: [dma 4]
[    1.252365] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.252384] pnp 00:05: [io  0x0061]
[    1.252454] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    1.252479] pnp 00:06: [io  0x00f0]
[    1.252497] pnp 00:06: [irq 13]
[    1.252573] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.252594] pnp 00:07: [io  0x0070-0x0071]
[    1.252604] pnp 00:07: [irq 8]
[    1.252675] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.252696] pnp 00:08: [io  0x0060]
[    1.252700] pnp 00:08: [io  0x0064]
[    1.252710] pnp 00:08: [irq 1]
[    1.252777] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.252802] pnp 00:09: [irq 12]
[    1.252881] pnp 00:09: Plug and Play ACPI device, IDs LEN0020 PNP0f13 (active)
[    1.252975] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    1.253051] pnp 00:0a: Plug and Play ACPI device, IDs SMO1200 PNP0c31 (active)
[    1.253958] pnp: PnP ACPI: found 11 devices
[    1.253962] ACPI: ACPI bus type pnp unregistered
[    1.253986] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    1.253993] system 00:00: [mem 0x000c0000-0x000c3fff] has been reserved
[    1.253999] system 00:00: [mem 0x000c4000-0x000c7fff] has been reserved
[    1.254010] system 00:00: [mem 0x000c8000-0x000cbfff] has been reserved
[    1.254016] system 00:00: [mem 0x000cc000-0x000cffff] has been reserved
[    1.254022] system 00:00: [mem 0x000d0000-0x000d3fff] has been reserved
[    1.254028] system 00:00: [mem 0x000d4000-0x000d7fff] has been reserved
[    1.254034] system 00:00: [mem 0x000d8000-0x000dbfff] has been reserved
[    1.254040] system 00:00: [mem 0x000dc000-0x000dffff] has been reserved
[    1.254047] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
[    1.254053] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
[    1.254060] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
[    1.254066] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
[    1.254072] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    1.254079] system 00:00: [mem 0x00100000-0xdf9fffff] could not be reserved
[    1.254086] system 00:00: [mem 0xfec00000-0xfed3ffff] could not be reserved
[    1.254092] system 00:00: [mem 0xfed4c000-0xffffffff] could not be reserved
[    1.254110] system 00:02: [io  0x0400-0x047f] has been reserved
[    1.254116] system 00:02: [io  0x0500-0x057f] has been reserved
[    1.254122] system 00:02: [io  0x0800-0x080f] has been reserved
[    1.254128] system 00:02: [io  0x15e0-0x15ef] has been reserved
[    1.254134] system 00:02: [io  0x1600-0x167f] has been reserved
[    1.254142] system 00:02: [mem 0xf8000000-0xfbffffff] has been reserved
[    1.254148] system 00:02: [mem 0x00000000-0x00000fff] could not be reserved
[    1.254154] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.254161] system 00:02: [mem 0xfed10000-0xfed13fff] has been reserved
[    1.254167] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.254174] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.254180] system 00:02: [mem 0xfed45000-0xfed4bfff] has been reserved
[    1.262186] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.262191] pci 0000:00:1c.0:   bridge window [io  disabled]
[    1.262203] pci 0000:00:1c.0:   bridge window [mem disabled]
[    1.262213] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    1.262228] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    1.262233] pci 0000:00:1c.1:   bridge window [io  disabled]
[    1.262245] pci 0000:00:1c.1:   bridge window [mem 0xf2500000-0xf25fffff]
[    1.262255] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    1.262270] pci 0000:00:1c.3: PCI bridge to [bus 05-0c]
[    1.262277] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    1.262289] pci 0000:00:1c.3:   bridge window [mem 0xf1d00000-0xf24fffff]
[    1.262300] pci 0000:00:1c.3:   bridge window [mem 0xf0400000-0xf0bfffff 64bit pref]
[    1.262315] pci 0000:00:1c.4: PCI bridge to [bus 0d-0d]
[    1.262322] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    1.262334] pci 0000:00:1c.4:   bridge window [mem 0xf1500000-0xf1cfffff]
[    1.262344] pci 0000:00:1c.4:   bridge window [mem 0xf0c00000-0xf13fffff 64bit pref]
[    1.262359] pci 0000:00:1c.6: PCI bridge to [bus 0e-0e]
[    1.262363] pci 0000:00:1c.6:   bridge window [io  disabled]
[    1.262375] pci 0000:00:1c.6:   bridge window [mem 0xf1400000-0xf14fffff]
[    1.262384] pci 0000:00:1c.6:   bridge window [mem pref disabled]
[    1.262423] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.262437] pci 0000:00:1c.0: setting latency timer to 64
[    1.262457] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.262467] pci 0000:00:1c.1: setting latency timer to 64
[    1.262487] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.262496] pci 0000:00:1c.3: setting latency timer to 64
[    1.262511] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.262520] pci 0000:00:1c.4: setting latency timer to 64
[    1.262537] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.262547] pci 0000:00:1c.6: setting latency timer to 64
[    1.262556] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.262561] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.262566] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.262572] pci_bus 0000:00: resource 7 [mem 0xdfa00000-0xfebfffff]
[    1.262577] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed4bfff]
[    1.262583] pci_bus 0000:03: resource 1 [mem 0xf2500000-0xf25fffff]
[    1.262589] pci_bus 0000:05: resource 0 [io  0x4000-0x4fff]
[    1.262594] pci_bus 0000:05: resource 1 [mem 0xf1d00000-0xf24fffff]
[    1.262599] pci_bus 0000:05: resource 2 [mem 0xf0400000-0xf0bfffff 64bit pref]
[    1.262605] pci_bus 0000:0d: resource 0 [io  0x3000-0x3fff]
[    1.262610] pci_bus 0000:0d: resource 1 [mem 0xf1500000-0xf1cfffff]
[    1.262615] pci_bus 0000:0d: resource 2 [mem 0xf0c00000-0xf13fffff 64bit pref]
[    1.262621] pci_bus 0000:0e: resource 1 [mem 0xf1400000-0xf14fffff]
[    1.262684] NET: Registered protocol family 2
[    1.263071] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.265695] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.269118] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.269498] TCP: Hash tables configured (established 524288 bind 65536)
[    1.269503] TCP reno registered
[    1.269527] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.269582] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.269786] NET: Registered protocol family 1
[    1.269817] pci 0000:00:02.0: Boot video device
[    1.270233] PCI: CLS 64 bytes, default 64
[    1.270322] Trying to unpack rootfs image as initramfs...
[    2.209628] Freeing initrd memory: 17008k freed
[    2.215409] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.215419] Placing 64MB software IO TLB between ffff88001bc00000 - ffff88001fc00000
[    2.215424] software IO TLB at phys 0x1bc00000 - 0x1fc00000
[    2.216130] Scanning for low memory corruption every 60 seconds
[    2.216402] audit: initializing netlink socket (disabled)
[    2.216422] type=2000 audit(1319319577.060:1): initialized
[    2.255670] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.259458] VFS: Disk quotas dquot_6.5.2
[    2.259587] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.260922] fuse init (API version 7.15)
[    2.261109] msgmni has been set to 7685
[    2.261566] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.261572] io scheduler noop registered
[    2.261576] io scheduler deadline registered
[    2.261656] io scheduler cfq registered (default)
[    2.265526] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.265584] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.265772] intel_idle: MWAIT substates: 0x21120
[    2.265776] intel_idle: v0.4 model 0x2A
[    2.265780] intel_idle: lapic_timer_reliable_states 0xffffffff
[    2.266322] ACPI: AC Adapter [AC] (off-line)
[    2.266792] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    2.267030] ACPI: Lid Switch [LID]
[    2.267130] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    2.267140] ACPI: Sleep Button [SLPB]
[    2.267254] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    2.267261] ACPI: Power Button [PWRF]
[    2.267549] ACPI: acpi_idle yielding to intel_idle
[    2.273639] thermal LNXTHERM:00: registered as thermal_zone0
[    2.273645] ACPI: Thermal Zone [THM0] (34 C)
[    2.273803] ERST: Table is not found!
[    2.274753] Linux agpgart interface v0.103
[    2.275380] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    2.275881] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    2.279901] agpgart-intel 0000:00:00.0: detected 65536K stolen memory, trimming to 32768K
[    2.369310] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    2.369382] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.790040] ACPI: Battery Slot [BAT0] (battery present)
[    2.795611] serial 0000:00:16.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.816120] 0000:00:16.3: ttyS4 at I/O 0x50b0 (irq = 19) is a 16550A
[    2.818625] brd: module loaded
[    2.819707] loop: module loaded
[    2.820717] Fixed MDIO Bus: probed
[    2.820778] PPP generic driver version 2.4.2
[    2.820855] tun: Universal TUN/TAP device driver, 1.6
[    2.820859] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.821009] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.821257] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    2.821456] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    2.821470] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.821513] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.821521] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.821602] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.822584] ehci_hcd 0000:00:1a.0: debug port 2
[    2.826460] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.826497] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf262a000
[    2.842480] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.842753] hub 1-0:1.0: USB hub found
[    2.842763] hub 1-0:1.0: 3 ports detected
[    2.843119] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    2.843320] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    2.843346] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.843378] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.843385] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.843477] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.892403] ehci_hcd 0000:00:1d.0: debug port 2
[    2.896295] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.896328] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf2629000
[    2.912313] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.912540] hub 2-0:1.0: USB hub found
[    2.912549] hub 2-0:1.0: 3 ports detected
[    2.912683] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.912707] uhci_hcd: USB Universal Host Controller Interface driver
[    2.912933] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    2.916226] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.916240] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.916381] mice: PS/2 mouse device common for all mice
[    2.916642] rtc_cmos 00:07: RTC can wake from S4
[    2.916790] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.916849] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.917074] device-mapper: uevent: version 1.0.3
[    2.917317] device-mapper: ioctl: 4.18.0-ioctl (2010-06-29) initialised: dm-devel@redhat.com
[    2.917439] device-mapper: multipath: version 1.1.1 loaded
[    2.917445] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.917986] cpuidle: using governor ladder
[    2.918433] cpuidle: using governor menu
[    2.918983] TCP cubic registered
[    2.919253] NET: Registered protocol family 10
[    2.919988] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.919994] lo: Disabled Privacy Extensions
[    2.920415] NET: Registered protocol family 17
[    2.920451] Registering the dns_resolver key type
[    2.924538] PM: Hibernation image not present or could not be loaded.
[    2.924544] registered taskstats version 1
[    2.924978]   Magic number: 15:40:703
[    2.925048] rtc_cmos 00:07: setting system clock to 2011-10-22 21:39:38 UTC (1319319578)
[    2.925050] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.925051] EDD information not available.
[    2.925109] Freeing unused kernel memory: 1012k freed
[    2.925264] Write protecting the kernel read-only data: 10240k
[    2.925414] Freeing unused kernel memory: 288k freed
[    2.925568] Freeing unused kernel memory: 1484k freed
[    2.935470] udev[72]: starting version 163
[    2.963385] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.7-k2
[    2.963388] e1000e: Copyright (c) 1999 - 2010 Intel Corporation.
[    2.963425] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.963436] e1000e 0000:00:19.0: setting latency timer to 64
[    2.963627] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[    2.985912] [drm] Initialized drm 1.1.0 20060810
[    3.161835] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    3.205318] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) f0:de:f1:96:3d:03
[    3.205321] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.205371] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: 1000ff-0ff
[    3.205408] i915 0000:00:02.0: power state changed by ACPI to D0
[    3.205416] i915 0000:00:02.0: power state changed by ACPI to D0
[    3.205422] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.205425] i915 0000:00:02.0: setting latency timer to 64
[    3.226370] mtrr: no more MTRRs available
[    3.226372] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    3.226687] i915 0000:00:02.0: irq 41 for MSI/MSI-X
[    3.311872] hub 1-1:1.0: USB hub found
[    3.311976] hub 1-1:1.0: 6 ports detected
[    3.431115] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    3.444346] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.581212] hub 2-1:1.0: USB hub found
[    3.581306] hub 2-1:1.0: 8 ports detected
[    3.660609] usb 1-1.6: new high speed USB device using ehci_hcd and address 3
[    3.745818] Console: switching to colour frame buffer device 170x48
[    3.748119] fb0: inteldrmfb frame buffer device
[    3.748120] drm: registered panic notifier
[    3.791853] acpi device:01: registered as cooling_device4
[    3.792130] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    3.792168] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    3.792296] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.792314] ahci 0000:00:1f.2: version 3.0
[    3.792325] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.792370] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    3.792402] ahci: SSS flag set, parallel bus scan disabled
[    3.810387] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x13 impl SATA mode
[    3.810400] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems sxs apst 
[    3.810404] ahci 0000:00:1f.2: setting latency timer to 64
[    3.850766] scsi0 : ahci
[    3.850909] scsi1 : ahci
[    3.851058] scsi2 : ahci
[    3.851209] scsi3 : ahci
[    3.851360] scsi4 : ahci
[    3.851433] scsi5 : ahci
[    3.851787] ata1: SATA max UDMA/133 abar m2048@0xf2628000 port 0xf2628100 irq 42
[    3.851790] ata2: SATA max UDMA/133 abar m2048@0xf2628000 port 0xf2628180 irq 42
[    3.851791] ata3: DUMMY
[    3.851792] ata4: DUMMY
[    3.851794] ata5: SATA max UDMA/133 abar m2048@0xf2628000 port 0xf2628300 irq 42
[    3.851795] ata6: DUMMY
[    4.199432] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.200492] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    4.200504] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    4.200512] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    4.201463] ata1.00: ATA-8: HITACHI HTS723232A7A364, EC2ZB70R, max UDMA/100
[    4.201473] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    4.202610] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    4.202622] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    4.202630] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    4.203560] ata1.00: configured for UDMA/100
[    4.203724] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS72323 EC2Z PQ: 0 ANSI: 5
[    4.203868] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.203886] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    4.203919] sd 0:0:0:0: [sda] Write Protect is off
[    4.203922] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.203936] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.265732]  sda: sda1 sda2 < sda5 >
[    4.266028] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.568573] ata2: SATA link down (SStatus 0 SControl 300)
[    4.917768] ata5: SATA link down (SStatus 0 SControl 300)
[    5.665050] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    5.665055] EXT4-fs (sda1): write access will be enabled during recovery
[    5.987874] EXT4-fs (sda1): recovery complete
[    5.988510] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.977267] Adding 11533308k swap on /dev/sda5.  Priority:-1 extents:1 across:11533308k 
[    9.144313] udev[353]: starting version 163
[    9.213270] EXT4-fs (sda1): warning: maximal mount count reached, running e2fsck is recommended
[    9.374820] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.897398] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.928130] lp: driver loaded but no devices found
[   11.138488] ip_tables: (C) 2000-2006 Netfilter Core Team
[   11.150097] tpm_tis 00:0a: 1.2 TPM (device-id 0x0, rev-id 78)
[   11.150639] cfg80211: Calling CRDA to update world regulatory domain
[   11.189849] type=1400 audit(1319333986.770:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=549 comm="apparmor_parser"
[   11.189884] type=1400 audit(1319333986.770:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=549 comm="apparmor_parser"
[   11.189909] type=1400 audit(1319333986.770:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=549 comm="apparmor_parser"
[   11.192036] type=1400 audit(1319333986.770:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=512 comm="apparmor_parser"
[   11.192068] type=1400 audit(1319333986.770:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=512 comm="apparmor_parser"
[   11.192093] type=1400 audit(1319333986.770:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=512 comm="apparmor_parser"
[   11.262929] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   11.319157] Linux video capture interface: v2.00
[   11.460830] uvcvideo: Found UVC 1.00 device Integrated Camera (04f2:b217)
[   11.462406] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input5
[   11.462511] usbcore: registered new interface driver uvcvideo
[   11.462512] USB Video Class driver (v1.0.0)
[   11.496525] Synaptics Touchpad, model: 1, fw: 8.0, id: 0x1e2b1, caps: 0xd001a3/0x940300/0x120c00
[   11.496537] serio: Synaptics pass-through port at isa0060/serio1/input0
[   11.546639] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   12.025612] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.025614] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   12.025709] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.025764] iwlagn 0000:03:00.0: setting latency timer to 64
[   12.025911] iwlagn 0000:03:00.0: Detected 6000 Series 2x2 AGN Gen2a, REV=0xB0
[   12.036728] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[   12.036742] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   12.037024] iwlagn 0000:03:00.0: irq 43 for MSI/MSI-X
[   12.354581] cfg80211: World regulatory domain updated:
[   12.354585]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.354587]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.354590]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.354591]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.354593]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.354595]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.392382] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[   12.596640] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.596731] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   12.596849] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.639490] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   12.987025] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.009327] udev[362]: renamed network interface wlan0 to wlan1
[   14.215835] type=1400 audit(1319333989.800:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=872 comm="apparmor_parser"
[   14.215904] type=1400 audit(1319333989.800:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=872 comm="apparmor_parser"
[   14.523247] ppdev: user-space parallel port driver
[   16.002295] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[   16.062035] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[   16.062443] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.666028] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   17.396299] type=1400 audit(1319333992.990:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1103 comm="apparmor_parser"
[   17.396351] type=1400 audit(1319333992.990:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1103 comm="apparmor_parser"
[   17.396391] type=1400 audit(1319333992.990:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1103 comm="apparmor_parser"
[   17.416288] type=1400 audit(1319333993.010:13): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1102 comm="apparmor_parser"
[   17.444151] type=1400 audit(1319333993.040:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1108 comm="apparmor_parser"
[   17.450018] type=1400 audit(1319333993.050:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1106 comm="apparmor_parser"
[   17.450094] type=1400 audit(1319333993.050:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1106 comm="apparmor_parser"
[   17.871170] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   18.122953] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input7
[   19.494300] type=1400 audit(1319333995.100:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1104 comm="apparmor_parser"
[   19.494579] type=1400 audit(1319333995.100:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1104 comm="apparmor_parser"
[   19.494820] type=1400 audit(1319333995.100:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1104 comm="apparmor_parser"
[   22.061165] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[   29.338148] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[   40.518341] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]
[   40.567710] padlock: VIA PadLock not detected.
[  113.626661] wlan1: authenticate with 14:d6:4d:31:fd:c6 (try 1)
[  113.629578] wlan1: authenticated
[  113.634966] wlan1: waiting for beacon from 14:d6:4d:31:fd:c6
[  113.675052] wlan1: beacon received
[  113.676299] wlan1: associate with 14:d6:4d:31:fd:c6 (try 1)
[  113.680275] wlan1: RX AssocResp from 14:d6:4d:31:fd:c6 (capab=0x431 status=0 aid=1)
[  113.680284] wlan1: associated
[  113.688562] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  124.175487] wlan1: no IPv6 routers present
[ 1380.415299] lo: Disabled Privacy Extensions
[ 1387.070428] exe (2094): /proc/2094/oom_adj is deprecated, please use /proc/2094/oom_score_adj instead.
[ 1590.019983] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 1591.574645] wlan1: deauthenticating from 14:d6:4d:31:fd:c6 by local choice (reason=3)
[ 1591.645480] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1591.645502] cfg80211: Restoring regulatory settings
[ 1591.645517] cfg80211: Calling CRDA to update world regulatory domain
[ 1591.652828] cfg80211: World regulatory domain updated:
[ 1591.652836]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1591.652843]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1591.652849]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1591.652854]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1591.652860]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1591.652865]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1592.362045] PM: Syncing filesystems ... done.
[ 1592.363255] PM: Preparing system for mem sleep
[ 1592.565643] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 1592.584645] Freezing remaining freezable tasks ... (elapsed 0.02 seconds) done.
[ 1592.604718] PM: Entering mem sleep
[ 1592.604803] Suspending console(s) (use no_console_suspend to debug)
[ 1592.780726] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 1592.780852] sd 0:0:0:0: [sda] Stopping disk
[ 1593.043817] ehci_hcd 0000:00:1d.0: PCI INT A disabled
[ 1593.043954] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[ 1593.044588] ACPI handle has no context!
[ 1593.103428] i915 0000:00:02.0: power state changed by ACPI to D3
[ 1593.152185] e1000e 0000:00:19.0: PCI INT A disabled
[ 1593.152191] e1000e 0000:00:19.0: PME# enabled
[ 1593.152197] e1000e 0000:00:19.0: wake-up capability enabled by ACPI
[ 1593.263237] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 1593.283190] PM: suspend of devices complete after 679.852 msecs
[ 1593.283192] PM: suspend devices took 0.680 seconds
[ 1593.323076] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D3
[ 1593.362984] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D3
[ 1593.363035] PM: late suspend of devices complete after 80.025 msecs
[ 1593.363237] ACPI: Preparing to enter system sleep state S3
[ 1593.792001] PM: Saving platform NVS memory
[ 1593.802983] Disabling non-boot CPUs ...
[ 1593.812104] Broke affinity for irq 43
[ 1593.921591] CPU 1 is now offline
[ 1594.200944] CPU 2 is now offline
[ 1594.221032] Broke affinity for irq 1
[ 1594.221065] Broke affinity for irq 16
[ 1594.221076] Broke affinity for irq 42
[ 1594.330654] CPU 3 is now offline
[ 1594.330660] SMP alternatives: switching to UP code
[ 1594.334504] Extended CMOS year: 2000
[ 1594.334870] Back to C!
[ 1594.334877] PM: Restoring platform NVS memory
[ 1594.350445] Extended CMOS year: 2000
[ 1594.350505] Enabling non-boot CPUs ...
[ 1594.350641] SMP alternatives: switching to SMP code
[ 1594.354963] Booting Node 0 Processor 1 APIC 0x1
[ 1594.606180] CPU1 is up
[ 1594.606331] Booting Node 0 Processor 2 APIC 0x2
[ 1594.865504] CPU2 is up
[ 1594.865572] Booting Node 0 Processor 3 APIC 0x3
[ 1595.125002] CPU3 is up
[ 1595.126862] ACPI: Waking up from system sleep state S3
[ 1595.603817] ACPI: \_SB_.PCI0.LPC_.EC__.BAT1 - docking
[ 1595.673640] ACPI: Unable to dock!
[ 1595.953013] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1595.953020] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[ 1595.953036] pci 0000:00:16.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1595.953048] pci 0000:00:16.0: restoring config space at offset 0x4 (was 0xfed0a004, writing 0xf2625004)
[ 1595.953054] pci 0000:00:16.0: restoring config space at offset 0x1 (was 0x100006, writing 0x180006)
[ 1595.953070] serial 0000:00:16.3: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[ 1595.953082] serial 0000:00:16.3: restoring config space at offset 0x5 (was 0x0, writing 0xf262c000)
[ 1595.953085] serial 0000:00:16.3: restoring config space at offset 0x4 (was 0x1, writing 0x50b1)
[ 1595.953091] serial 0000:00:16.3: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00007)
[ 1595.953108] e1000e 0000:00:19.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 1595.953118] e1000e 0000:00:19.0: restoring config space at offset 0x6 (was 0x1, writing 0x5081)
[ 1595.953125] e1000e 0000:00:19.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100007)
[ 1595.953147] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1595.953161] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x4 (was 0x0, writing 0xf262a000)
[ 1595.953167] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[ 1595.972937] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1595.992894] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1595.992916] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1595.992928] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0xf2620004)
[ 1595.992932] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1595.992936] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
[ 1595.992971] pci 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1595.992984] pci 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 1595.992989] pci 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
[ 1595.992994] pci 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
[ 1595.993004] pci 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 1595.993011] pci 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100004)
[ 1595.993056] pci 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x207)
[ 1595.993069] pci 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 1595.993074] pci 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xf250f250)
[ 1595.993079] pci 0000:00:1c.1: restoring config space at offset 0x7 (was 0x0, writing 0x200000f0)
[ 1595.993089] pci 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 1595.993096] pci 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 1595.993140] pci 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x40b)
[ 1595.993153] pci 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xf0b1f041)
[ 1595.993158] pci 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xf240f1d0)
[ 1595.993163] pci 0000:00:1c.3: restoring config space at offset 0x7 (was 0x20000000, writing 0x4040)
[ 1595.993172] pci 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 1595.993178] pci 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 1595.993214] pci 0000:00:1c.4: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1595.993222] pci 0000:00:1c.4: restoring config space at offset 0x9 (was 0x10001, writing 0xf131f0c1)
[ 1595.993226] pci 0000:00:1c.4: restoring config space at offset 0x8 (was 0x0, writing 0xf1c0f150)
[ 1595.993230] pci 0000:00:1c.4: restoring config space at offset 0x7 (was 0x20000000, writing 0x3030)
[ 1595.993236] pci 0000:00:1c.4: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 1595.993241] pci 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 1595.993266] pci 0000:00:1c.6: restoring config space at offset 0xf (was 0x300, writing 0x307)
[ 1595.993275] pci 0000:00:1c.6: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 1595.993278] pci 0000:00:1c.6: restoring config space at offset 0x8 (was 0x0, writing 0xf140f140)
[ 1595.993282] pci 0000:00:1c.6: restoring config space at offset 0x7 (was 0x0, writing 0x200000f0)
[ 1595.993288] pci 0000:00:1c.6: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 1595.993293] pci 0000:00:1c.6: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 1595.993317] ehci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 1595.993331] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x4 (was 0x0, writing 0xf2629000)
[ 1595.993337] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[ 1596.012846] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[ 1596.032800] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[ 1596.032863] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00403, writing 0x2b00407)
[ 1596.033032] iwlagn 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
[ 1596.033160] iwlagn 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf2500004)
[ 1596.033194] iwlagn 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1596.033238] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 1596.033456] pci 0000:0d:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[ 1596.033493] pci 0000:0d:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[ 1596.033550] pci 0000:0e:00.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
[ 1596.033571] pci 0000:0e:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf1400004)
[ 1596.033576] pci 0000:0e:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1596.033583] pci 0000:0e:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 1596.033648] PM: early resume of devices complete after 80.849 msecs
[ 1596.033732] i915 0000:00:02.0: power state changed by ACPI to D0
[ 1596.033754] e1000e 0000:00:19.0: wake-up capability disabled by ACPI
[ 1596.033758] e1000e 0000:00:19.0: PME# disabled
[ 1596.033775] i915 0000:00:02.0: power state changed by ACPI to D0
[ 1596.033812] i915 0000:00:02.0: setting latency timer to 64
[ 1596.033830] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[ 1596.034053] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 1596.034058] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 1596.034114] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[ 1596.034165] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1596.034169] pci 0000:00:1c.0: setting latency timer to 64
[ 1596.034176] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 1596.034181] pci 0000:00:1c.1: setting latency timer to 64
[ 1596.034215] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[ 1596.034220] pci 0000:00:1c.3: setting latency timer to 64
[ 1596.034228] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1596.034234] pci 0000:00:1c.4: setting latency timer to 64
[ 1596.034241] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 1596.034244] pci 0000:00:1c.6: setting latency timer to 64
[ 1596.034423] ahci 0000:00:1f.2: setting latency timer to 64
[ 1596.034867] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1596.034945] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[ 1596.035053] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[ 1596.035060] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 1596.035066] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[ 1596.035268] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1596.035273] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1596.035278] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[ 1596.052687] sd 0:0:0:0: [sda] Starting disk
[ 1596.322261] usb 1-1.6: reset high speed USB device using ehci_hcd and address 3
[ 1596.421845] ata5: SATA link down (SStatus 0 SControl 300)
[ 1596.461744] ata2: SATA link down (SStatus 0 SControl 300)
[ 1596.840856] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1596.842012] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[ 1596.842022] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 1596.842030] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 1596.844291] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[ 1596.844301] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 1596.844308] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 1596.845331] ata1.00: configured for UDMA/100
[ 1596.882228] PM: resume of devices complete after 850.520 msecs
[ 1596.882353] PM: resume devices took 0.850 seconds
[ 1596.882654] PM: Finishing wakeup.
[ 1596.882655] Restarting tasks ... done.
[ 1596.882998] video LNXVIDEO:00: Restoring backlight state
[ 1597.020479] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[ 1597.080254] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[ 1597.080672] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1597.186511] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1597.904500] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[ 1603.694468] wlan1: authenticate with 14:d6:4d:31:fd:c6 (try 1)
[ 1603.697346] wlan1: authenticated
[ 1603.702936] wlan1: waiting for beacon from 14:d6:4d:31:fd:c6
[ 1603.745885] wlan1: beacon received
[ 1603.745938] wlan1: associate with 14:d6:4d:31:fd:c6 (try 1)
[ 1603.749937] wlan1: RX AssocResp from 14:d6:4d:31:fd:c6 (capab=0x431 status=0 aid=1)
[ 1603.749946] wlan1: associated
[ 1603.757747] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1613.994410] wlan1: no IPv6 routers present
```I don't know if this helps, but here is the output of loading the modules manually:

[B]carlos@X220:~$ sudo modprobe -v vboxpci
FATAL: Module vboxpci not found.
carlos@X220:~$ sudo modprobe -v vboxnetadp
FATAL: Module vboxnetadp not found.
carlos@X220:~$ sudo modprobe -v vboxnetflt
FATAL: Module vboxnetflt not found.
carlos@X220:~$ sudo modprobe -v vboxdrv
FATAL: Module vboxdrv not found.
[/B]
I am a member of vboxusers.

I truly appreciate the help!

Thanks,
Carlos

---

### Post by deloquencia on 2011-10-24
modprobe can't find any modules, so during the installation von virtualbox they haven't been compiled. dmesg won't help here, please check the file **/var/log/vbox-install.log**.

It could be that you don't have kernel headers or some required other package, but with the installation of dkms usually all necessary packages for compiling kernel headers are installed.

try to run:

[B]
sudo dpkg -l linux-headers-*
sudo cat /var/log/vbox-install.log
[/B]

I think we're getting closer to the problem :)

---

### Post by pcarlos853 on 2011-10-24
Again thanks for you help!

I think that you are right with the possibility of missing headers (I don't know much about the kernel). Anyway here is the output below:

** sudo dpkg -l linux-headers-***

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                                                                      Description
+++-====================================-============================================================================-==============================================================================
un  linux-headers-2.6                    <none>                                                                       (no description available)
un  linux-headers-2.6-686                <none>                                                                       (no description available)
un  linux-headers-2.6-amd64              <none>                                                                       (no description available)
un  linux-headers-2.6.35-22              <none>                                                                       (no description available)
un  linux-headers-2.6.35-22-generic      <none>                                                                       (no description available)
ii  linux-headers-2.6.35-30              2.6.35-30.60                                                                 Header files related to Linux kernel version 2.6.35
ii  linux-headers-2.6.35-30-generic      2.6.35-30.60                                                                 Linux kernel headers for version 2.6.35 on x86/x86_64
ii  linux-headers-2.6.36-020636          2.6.36-020636.201010210905                                                   Header files related to Linux kernel version 2.6.36
ii  linux-headers-2.6.36-020636-generic  2.6.36-020636.201010210905                                                   Linux kernel headers for version 2.6.36 on x86/x86_64
un  linux-headers-2.6.37-020637          <none>                                                                       (no description available)
un  linux-headers-2.6.37-020637-generic  <none>                                                                       (no description available)
ii  linux-headers-generic                2.6.35.30.38                                                                 Generic Linux kernel headers
```

[B] sudo cat /var/log/vbox-install.log

[/B]```
Uninstalling modules from DKMS
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/4.1.4/source ->
                 /usr/src/vboxhost-4.1.4

DKMS: add Completed.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.37-020637-generic package.
Failed to install using DKMS, attempting to install without
Makefile:172: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
```

Thanks so much for the help!
Carlos

---

### Post by deloquencia on 2011-10-25
That's it :)

your system is missing the right kernel header package. It's the package **linux-headers-2.6.37-020637-generic**. Only some old package for the kernel 2.6.35 and 2.6.36 are currently installed.

So just run apt-get to install the new package, corresponding your new kernel 2.6.37:

**sudo apt-get install linux-headers-2.6.37-020637-generic**

... and then rerun vboxdrv with the parameter *setup*:

**sudo /etc/init.d/vboxdrv setup**

The modules should compile and be loaded. Than you can start Virtual Machines using virtualbox.


Just in any case run afterwards:
**sudo cat /var/log/vbox-install.log**
if something odd should happen, but I believe it should not happen and it'll work :)

---

### Post by pcarlos853 on 2011-10-25
Again thanks so much for the help, but I cant install the headers. I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-2.6.37-020637-generic
E: Couldn't find any package by regex 'linux-headers-2.6.37-020637-generic'
```Would I need to add a repository or install it manually?

Thanks!
Carlos

---

### Post by deloquencia on 2011-10-27
That's strange, because the package linux-headers-2.6.37-020637-generic is listed in your apt cache, like you tested it before with **dpkg -l linux-headers-***

Now I searched for it at [packages.ubuntu.com]("http://packages.ubuntu.com/search?keywords=linux-headers-2.6.37&searchon=names&suite=all&section=all") and at [http://www.ubuntuupdates.org/](http://www.ubuntuupdates.org/) - there are only such packages for Lucid (10.04) and any for Maverick (10.10). Also I checked Debian packages at [http://packages.debian.org]("http://packages.debian.org/search?keywords=linux-headers-2.6.37&searchon=names&suite=all&section=all") - nothing... %|

From where you've got this kernel in first hand? Did you add some repositories apart from canonical, universe or multiverse?

Try to update the cache of apt with
**sudo apt-get update**
After updating check again the cache with
**dpkg -l linux-headers-***

Is this package still there?
When it is what's in your sources.list?
**sudo cat /etc/apt/sources.list | grep -v -e "#.*"**

The last shot which I can think of is skip apt-get and dkms, install manualy the source code of 2.6.37, point make to that directory and compile the modules.

1. Get the source at [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.37.6.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.37.6.tar.bz2)
2. Unpack it at /usr/src/ with tar -xjvf
3. Change to the directory at /usr/share/virtualbox/src/vboxhost

At this point I'm not sure anymore how to proceed - sorry. Either you edit the Makefiles in the directories vboxdrv, vboxnetadp, vboxnetflt, vboxpci and add a variable KERN_DIR="/usr/src/linux-2.6.37.6". Or you only create a soft link to that directory with the name "linux" in /usr/src.

Just try both and than run **sudo make && sudo make install** in the directory /usr/share/virtualbox/src/vboxhost.


Too much hassle - good luck :)


Did you thought about making a flavor upgrade to Ubuntu Oneiric (11.10) or Ubuntu Natty (11.04)? Could spare you this and future hassle with going without dkms. Why did you upgrade your kernel and didn't stay with 2.6.35?

---

