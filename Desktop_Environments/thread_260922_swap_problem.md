---
title: "swap problem"
date: 2006-09-19
forum: Desktop Environments
---

### Post by radino on 2006-09-19
Hi, 
I have following problem.
I have 2 swap partitions

radino@sunka:~$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       1052216 0       -1
/dev/sdb5                               partition       1052216 0       -2


When PC starts to swap, I get kernel oops, when PC try to allocate more than 19-20M of swap.:

Sep 19 19:40:38 sunka kernel: [17245814.336000] Unable to handle kernel paging request at virtual address a081fbf8
Sep 19 19:40:38 sunka kernel: [17245814.336000]  printing eip:
Sep 19 19:40:38 sunka kernel: [17245814.336000] f89bd0f4
Sep 19 19:40:38 sunka kernel: [17245814.336000] *pde = 00000000
Sep 19 19:40:38 sunka kernel: [17245814.336000] Oops: 0002 [#1]
Sep 19 19:40:38 sunka kernel: [17245814.336000] PREEMPT
Sep 19 19:40:38 sunka kernel: [17245814.336000] Modules linked in: nls_cp437 isofs udf rfcomm l2cap bluetooth tun cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table tc1100_wmi video acpi_sbs battery i2c_acpi_ec container button pcc_acpi sony_acpi ac dev_acpi hotkey ipv6 dm_mod lp snd_mpu401 snd_mpu401_uart snd_rawmidi snd_seq_device analog gameport parport_pc parport rtc nvidia agpgart pcspkr floppy psmouse serio_raw shpchp pci_hotplug snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore i2c_nforce2 snd_page_alloc i2c_core af_packet sg tsdev evdev reiserfs raid0 raid1 md_mod usbhid ide_generic forcedeth ehci_hcd ohci_hcd usbcore ide_cd cdrom sd_mod sata_nv libata scsi_mod generic amd74xx thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Sep 19 19:40:38 sunka kernel: [17245814.336000] CPU:    0
Sep 19 19:40:38 sunka kernel: [17245814.336000] EIP:    0060:[pg0+945369332/1069368320]    Tainted: P      VLI
Sep 19 19:40:38 sunka kernel: [17245814.336000] EFLAGS: 00210282   (2.6.15-26-386)
Sep 19 19:40:38 sunka kernel: [17245814.336000] EIP is at reiserfs_free_jh+0x14/0x60 [reiserfs]
Sep 19 19:40:38 sunka kernel: [17245814.336000] eax: a3920321   ebx: a081fbf4   ecx: f89a5bb0   edx: c14abc80
Sep 19 19:40:38 sunka kernel: [17245814.336000] esi: e7f7f754   edi: c14abc80   ebp: dfeb5f78   esp: dfeb5e30
Sep 19 19:40:38 sunka kernel: [17245814.336000] ds: 007b   es: 007b   ss: 0068
Sep 19 19:40:38 sunka kernel: [17245814.336000] Process kswapd0 (pid: 168, threadinfo=dfeb4000 task=dfea7550)
Sep 19 19:40:38 sunka kernel: [17245814.336000] Stack: e7f7f754 e7f7f754 f89a5bf9 e7f7f754 c14abc80 dfeb5f14 d2048f40 c014b8e7
Sep 19 19:40:38 sunka kernel: [17245814.336000]        c14abc80 000000d0 00000002 00000012 00000001 00000000 00000004 00000001
Sep 19 19:40:38 sunka kernel: [17245814.336000]        c13cffa0 c113f4a0 c1093480 c10d1c20 c1125e60 c119bf40 c16c65e0 c15b3bc0
Sep 19 19:40:38 sunka kernel: [17245814.336000] Call Trace:
Sep 19 19:40:38 sunka kernel: [17245814.336000]  [pg0+945273849/1069368320] reiserfs_releasepage+0x49/0xb0 [reiserfs]
Sep 19 19:40:38 sunka kernel: [17245814.336000]  [shrink_list+1015/1200] shrink_list+0x3f7/0x4b0
Sep 19 19:40:38 sunka kernel: [17245814.336000]  [shrink_cache+256/784] shrink_cache+0x100/0x310
Sep 19 19:40:38 sunka kernel: [17245814.336000]  [get_dirty_limits+23/304] get_dirty_limits+0x17/0x130
Sep 19 19:40:38 sunka kernel: [17245814.336000]  [shrink_zone+142/240] shrink_zone+0x8e/0xf0
Sep 19 19:40:38 sunka kernel: [17245814.336000]  [balance_pgdat+652/1040] balance_pgdat+0x28c/0x410
Sep 19 19:40:38 sunka kernel: [17245814.336000]  [kswapd+198/272] kswapd+0xc6/0x110
Sep 19 19:40:38 sunka kernel: [17245814.336000]  [autoremove_wake_function+0/64] autoremove_wake_function+0x0/0x40
Sep 19 19:40:38 sunka kernel: [17245814.336000]  [kswapd+0/272] kswapd+0x0/0x110
Sep 19 19:40:38 sunka kernel: [17245814.336000]  [kernel_thread_helper+5/16] kernel_thread_helper+0x5/0x10
Sep 19 19:40:38 sunka kernel: [17245814.336000] Code: 87 33 c0 50 e8 8e bf 78 c7 5a 59 85 c0 74 e8 ff 05 84 95 9d f8 c3 90 56 53 8b 74 24 0c 8b 5e 28 85 db 74 3b c7 46 28 00 00 00 00 <c7> 43 04 00 00 00 00 8d 43 08 8b 4b 08 8b 50 04 89 51 04 89 0a
Sep 19 19:40:38 sunka kernel: [17245814.336000]  <6>note: kswapd0[168] exited with preempt_count 1

but when I tried this script:
radino@sunka:~$ cat a.sh
#!/bin/bash
$0

PC was able to allocate swap. 

I tried to recreate swap partitions: 
swapoff -a
mkswap /dev/sda5
mkswap /dev/sdb5
swapon -a

but It did not help. :(

I tried use only one swap partition 
swapoff -a
swap on /dev/sda5   # or /dev/sdb5

but It did not help. :(

PC configuration:
ASUS K8N4-E
2x WD 120 SATA
Inno3D 7300GS PCX
AMD Sempron 2600+ 64bit (Linux is 32bit)

kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/md0 ro quiet splash pci=nommconf

without pci=nommconf PC does not boot.

radino@sunka:~$ uname -a
Linux sunka 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 

OS: Ubuntu 6.06

I don't know what to do..  Could anybody help me, or give me any hint?****

---

### Post by tagra123 on 2006-09-19
This may be a dumb question, but is /dev/sdb5 really the swap partition?

---

### Post by radino on 2006-09-19
> This may be a dumb question, but is /dev/sdb5 really the swap partition?

It has to be:
swapoff -a
mkswap /dev/sda5
mkswap /dev/sdb5
swapon -a

but I'm sure, that it had been swap partition before I wrote these commands.

---

### Post by tagra123 on 2006-09-19
Please post the contents of /etc/fstab 


Possibly using the live CD -- reformat the swap (and only the swap partitions) I think gparted will let you do this.

Make sure to write down the partitions that gparted sees and what filesystems each partition is for.

Compare it to hd?/etc/fstab (if you are using the live cd you will need to mount the drive before doing this.

I'm stabbing in the dark here too.  I had a similar situatuon, but not exactly the same after editing the fstab once. ) I had mixed up the partitions.

---

### Post by radino on 2006-09-20
radino@sunka:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/md0        /               reiserfs notail          0       1
/dev/md3        /data           reiserfs defaults        0       2
/dev/md1        /home           reiserfs defaults        0       2
/dev/md4        /opt            reiserfs defaults        0       2
/dev/md2        /safedata       reiserfs defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/sdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

There are no mixed partitions on my PC. I am sure.
I have SW raid, so if the partitions were mixed, SW raid will be not functional..

radino@sunka:~$ cat /proc/mdstat
Personalities : [raid0] [raid1]
md4 : active raid0 sda7[0] sdb7[1]
      10474112 blocks 64k chunks

md3 : active raid0 sda6[0] sdb6[1]
      106526720 blocks 64k chunks

md2 : active raid1 sda3[0] sdb3[1]
      15727552 blocks [2/2] [UU]

md1 : active raid0 sda2[0] sdb2[1]
      62909952 blocks 256k chunks

md0 : active raid1 sda1[0] sdb1[1]
      10482304 blocks [2/2] [UU]


radino@sunka:~$ cat /proc/partitions
major minor  #blocks  name

   8     0  117220824 sda
   8     1   10482381 sda1
   8     2   31455270 sda2
   8     3   15727635 sda3
   8     4          1 sda4
   8     5    1052226 sda5
   8     6   53263476 sda6
   8     7    5237127 sda7
   8    16  117220824 sdb
   8    17   10482381 sdb1
   8    18   31455270 sdb2
   8    19   15727635 sdb3
   8    20          1 sdb4
   8    21    1052226 sdb5
   8    22   53263476 sdb6
   8    23    5237127 sdb7
   9     0   10482304 md0
   9     1   62909952 md1
   9     2   15727552 md2
   9     3  106526720 md3
   9     4   10474112 md4
 253     0   53263476 dm-0
 253     1   53263476 dm-1
 253     2  106526720 dm-2
 253     3    5237127 dm-3
 253     4    5237127 dm-4
 253     5   10474112 dm-5
 253     6    1052226 dm-6
 253     7    1052226 dm-7
 253     8   10482381 dm-8
 253     9   31455270 dm-9
 253    10   15727635 dm-10
 253    11   10482381 dm-11
 253    12   31455270 dm-12
 253    13   15727635 dm-13

every partition except swap is used in SW raid..

Swap is functional, but it behaves weird :(

---

### Post by tagra123 on 2006-09-20
You got me. Everything looks like it should work correctly.  I wonder if this has to do with raid in any way even though its not be used for swap.  

Sorry for the lack of help I could provide. Maybe there is something on bugzilla ?

---

