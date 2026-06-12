---
title: "huge kern.log and syslog files"
date: 2009-02-22
forum: General Help
---

### Post by olivine on 2009-02-22
My laptop (ibex with kernel 2.6.27-11 as far as I can tell) started acting in a weird way yesterday, with some programs not working, error messages I couldn't understand etc. It turns out the hardrive is nearly full, due to 3 huge files in /var/log: kern.log (4GB), syslog (4GB) and messages (3.7GB). The files filled up within a few minutes, starting with this in syslog:

Feb 21 17:17:01 Valpelline /USR/SBIN/CRON[30603]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 21 17:25:00 Valpelline kernel: [33760.053766] BUG: scheduling while atomic: swapper/0/0x00000100
Feb 21 17:25:00 Valpelline kernel: [33760.053779] Modules linked in: ipv6 af_packet i915 drm binfmt_misc rfcomm sco bridge stp bnep l2cap vboxdrv ppdev acpi_cpufreq cpufreq_powersave cpufreq_conservative cpufreq_stats cpufreq_userspace cpufreq_ondemand freq_table container sbs pci_slot sbshc iptable_filter ip_tables x_tables sbp2 parport_pc lp parport loop btusb bluetooth joydev snd_hda_intel dcdbas arc4 ecb crypto_blkcipher snd_pcm_oss snd_mixer_oss snd_pcm pcspkr iwlagn serio_raw snd_seq_dummy iwlcore psmouse snd_seq_oss rfkill snd_seq_midi snd_rawmidi snd_seq_midi_event led_class snd_seq mac80211 snd_timer snd_seq_device snd sdhci_pci cfg80211 sdhci soundcore ricoh_mmc mmc_core snd_page_alloc uvcvideo shpchp pci_hotplug compat_ioctl32 videodev v4l1_compat evdev video output battery button wmi ac intel_agp ext3 jbd mbcache sr_mod sd_mod crc_t10dif cdrom sg usbhid hid ahci libata scsi_mod dock ohci1394 ieee1394 ehci_hcd uhci_hcd usbcore e1000e thermal processor fan fbcon tileblit font bitblit softcursor fuse
Feb 21 17:25:00 Valpelline kernel: [33760.053963] CPU 1:
Feb 21 17:25:00 Valpelline kernel: [33760.053966] Modules linked in: ipv6 af_packet i915 drm binfmt_misc rfcomm sco bridge stp bnep l2cap vboxdrv ppdev acpi_cpufreq cpufreq_powersave cpufreq_conservative cpufreq_stats cpufreq_userspace cpufreq_ondemand freq_table container sbs pci_slot sbshc iptable_filter ip_tables x_tables sbp2 parport_pc lp parport loop btusb bluetooth joydev snd_hda_intel dcdbas arc4 ecb crypto_blkcipher snd_pcm_oss snd_mixer_oss snd_pcm pcspkr iwlagn serio_raw snd_seq_dummy iwlcore psmouse snd_seq_oss rfkill snd_seq_midi snd_rawmidi snd_seq_midi_event led_class snd_seq mac80211 snd_timer snd_seq_device snd sdhci_pci cfg80211 sdhci soundcore ricoh_mmc mmc_core snd_page_alloc uvcvideo shpchp pci_hotplug compat_ioctl32 videodev v4l1_compat evdev video output battery button wmi ac intel_agp ext3 jbd mbcache sr_mod sd_mod crc_t10dif cdrom sg usbhid hid ahci libata scsi_mod dock ohci1394 ieee1394 ehci_hcd uhci_hcd usbcore e1000e thermal processor fan fbcon tileblit font bitblit softcursor fuse
Feb 21 17:25:00 Valpelline kernel: [33760.054124] Pid: 0, comm: swapper Not tainted 2.6.27-9-generic #1
Feb 21 17:25:00 Valpelline kernel: [33760.054129] RIP: 0010:[<ffffffffa003ac09>]  [<ffffffffa003ac09>] acpi_idle_enter_bm+0x287/0x2d7 [processor]
Feb 21 17:25:00 Valpelline kernel: [33760.054152] RSP: 0018:ffff88011f055ea8  EFLAGS: 00000246
Feb 21 17:25:00 Valpelline kernel: [33760.054157] RAX: ffffffff807a1400 RBX: ffff88011f055ee8 RCX: 00001eb4603f38ae
[...]

I read through other threads with similar problems with kern.log0 and syslog.0. What can I do in this case? Thanks in advance for any help.

---

### Post by spiderbatdad on 2009-02-22
Not sure, but perhaps some boot options required to run on your hardware. Check dmesg.

---

### Post by spiderbatdad on 2009-02-22
This is possibly an acpi problem that can be fixed either in the system bios or with the boot option acpi=off, or noapci

---

### Post by olivine on 2009-02-22
Thanks for your help. I'll check the acpi thing in the bios. In the meantime, is there a way to reduce the size of these files? For instance by booting with a live cd and deleting parts of it? The files don't seem to be growing much bigger anymore.

Also, here's the output for dmesg (which I don't understand):

```
Log of dmesg 
Sun Feb 22 15:03:34 2009

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] Command line: root=UUID=760bd45b-91f0-49fe-824f-701f6aeb79fd ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
[    0.000000]  BIOS-e820: 000000000009bc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dd04d400 (usable)
[    0.000000]  BIOS-e820: 00000000dd04d400 - 00000000dd04f400 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dd04f400 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe60000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xdd04d max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00dd000000 page 2M
[    0.000000]  00dd000000 - 00dd04d000 page 4k
[    0.000000] kernel direct mapping tables up to dd04d000 @ 8000-e000
[    0.000000] last_map_addr: dd04d000 end: dd04d000
[    0.000000] init_memory_mapping
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ c000-12000
[    0.000000] last_map_addr: 120000000 end: 120000000
[    0.000000] RAMDISK: 377ab000 - 37fef07b
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000FB9F0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT DD051E00, 0074 (r1 DELL    M09     27D80A0A ASL        61)
[    0.000000] ACPI: FACP DD051C9C, 00F4 (r4 DELL    M09     27D80A0A ASL        61)
[    0.000000] ACPI: DSDT DD052400, 64B2 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS DD060C00, 0040
[    0.000000] ACPI: HPET DD051F00, 0038 (r1 DELL    M09            1 ASL        61)
[    0.000000] ACPI: ____ DD060400, 0030 (r1 DELL    M09     27D80A0A ASL        61)
[    0.000000] ACPI: APIC DD052000, 0068 (r1 DELL    M09     27D80A0A ASL        47)
[    0.000000] ACPI: ASF! DD051C00, 006A (r32 DELL    M09     27D80A0A ASL        61)
[    0.000000] ACPI: MCFG DD051FC0, 003E (r16 DELL    M09     27D80A0A ASL        61)
[    0.000000] ACPI: SLIC DD05209C, 0176 (r1 DELL    M09     27D80A0A ASL        61)
[    0.000000] ACPI: TCPA DD052300, 0032 (r1                        0 ASL         0)
[    0.000000] ACPI: BOOT DD051BC0, 0028 (r1 DELL    M09     27D80A0A ASL        61)
[    0.000000] ACPI: SSDT DD050331, 066C (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000d000 -  0000000000030fff] pages 24
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0120000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377ab000 - 0037fef07b]          RAMDISK ==> [00377ab000 - 0037fef07b]
[    0.000000]   #4 [000009bc00 - 0000100000]    BIOS reserved ==> [000009bc00 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
[    0.000000]   #6 [000000c000 - 000000d000]          PGTABLE ==> [000000c000 - 000000d000]
[    0.000000]  [ffffe20000000000-ffffe200047fffff] PMD -> [ffff880028200000-ffff88002c1fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000dd04d
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 1036264
[    0.000000]   DMA zone: 2103 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 884877 pages, LIFO batch:31
[    0.000000]   Normal zone: 129024 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000dd04d000 - 00000000dd04e000
[    0.000000] PM: Registered nosave memory: 00000000dd04e000 - 00000000dd04f000
[    0.000000] PM: Registered nosave memory: 00000000dd04f000 - 00000000dd050000
[    0.000000] PM: Registered nosave memory: 00000000dd050000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000feda0000
[    0.000000] PM: Registered nosave memory: 00000000feda0000 - 00000000feda6000
[    0.000000] PM: Registered nosave memory: 00000000feda6000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee10000
[    0.000000] PM: Registered nosave memory: 00000000fee10000 - 00000000ffe60000
[    0.000000] PM: Registered nosave memory: 00000000ffe60000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e2000000 (gap: e0000000:18000000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1016004
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=760bd45b-91f0-49fe-
Sun Feb 22 15:03:34 2009
----------------
```

---

### Post by spiderbatdad on 2009-02-22
not 100% sure but i think the options for your case are noapic nolapic pci=routeirq This you can add to /boot/grub/menu.lst at the end of your kernel line or after kopt= I prefer the first method. Shown in bold below.
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5bXXX ro **noapic nolapic pci=routeirq** 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

```You may have to try other combos...like just acpi=off

For the log files...yes you can delete them. Is your system unbootable? If you must use the live cd, you can mount your file system. You need to know the partition of your ubuntu installation. ```
sudo fdisk -l
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000021

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris
Sun Feb 22

```mount the file system from the live cd
```
sudo mount -t ext3 /dev/sda1 /mnt
cd /mnt/var/log
ls -l
sudo rm kern.log0 or whatever

```

---

### Post by olivine on 2009-02-22
No, the system boots fine. For some reason I thought I couldn't delete these files while on the system. I just truncated them following this thread:
[http://ubuntuforums.org/showthread.php?p=6200061#post6200061](http://ubuntuforums.org/showthread.php?p=6200061#post6200061)

Now I'll edit the grub menu.lst file following your directions and take it from there.

---

### Post by olivine on 2009-02-22
It turns out that I'm still running the 2.6.27-9 kernel. I have grub installed on a separate partition ([http://www.troubleshooters.com/linux/grub/grubpartition.htm#_Prerequisite](http://www.troubleshooters.com/linux/grub/grubpartition.htm#_Prerequisite)), and I didn't realize that I need to manually mount it and update menu.lst everytime the synaptic package manager downloads a new kernel (I guess, unless there's a better way).

In other words, the problem I have looks a bit like this one:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285)
I'll see if 2.6.27-11 fixes things. If not, I'll start messing with the acpi commands as you suggested, spiderbatdat. Thanks again for your advice.

---

