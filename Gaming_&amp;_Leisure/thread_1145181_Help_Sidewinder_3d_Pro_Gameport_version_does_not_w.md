---
title: "Help: Sidewinder 3d Pro Gameport version does not work"
date: 2009-05-01
forum: Gaming &amp; Leisure
---

### Post by sstakes1 on 2009-05-01
I've followed several threads here in these forums and elsewhere to get an old Gameport joystick (SideWinder 3d Pro) to work without much success

Here's my setup: A PCI soundcard with Gameport ( CMI8738 )
I do the following:

```
sudo modprobe joydump
sudo modprobe joydev
sudo modprobe snd_cmipci joystick_port=1
sudo modprobe sidewinder
```

When examining the system log I see
```

[  354.441974] C-Media PCI 0000:02:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[  354.461115] gameport: C-Media Gameport is pci0000:02:0a.0/gameport0, io 0x201, speed 59659kHz
[  354.461177] joydump: ,------------------ START ----------------.
[  354.461200] joydump: | Dumping:      pci0000:02:0a.0/gameport0 |
[  354.461204] joydump: | Speed:                        59659 kHz |
[  354.849276] joydump: >------------------ DATA -----------------<
[  354.849281] joydump: | index:   0 delta:   0 us data: 11110000 |
[  354.849290] joydump: | index:   1 delta:   0 us data: 11111111 |
[  354.849299] joydump: | index:   2 delta: 9760 us data: 11111001 |
[  354.849307] joydump: | index:   3 delta: 1888 us data: 11111000 |
[  354.849315] joydump: | index:   4 delta: 1170 us data: 11110000 |
[  354.849324] joydump: `------------------- END -----------------'

```

The logs show that the sound card and game port are recognized correctly. Yet no sign of joystick. Here is the lsmod in the situation where analog kernel module was loaded. I have also tried it with analog blacklisted.

```
Module                  Size  Used by
analog                 18592  0 
sidewinder             19200  0 
snd_cmipci             42016  2 
snd_opl3_lib           18560  1 snd_cmipci
snd_hwdep              15108  1 snd_opl3_lib
snd_mpu401_uart        15104  1 snd_cmipci
joydev                 18368  0 
joydump                11264  0 
gameport               19340  5 analog,sidewinder,snd_cmipci,joydump
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_cmipci,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_mpu401_uart,snd_seq_midi
k8temp                 12416  0 
ppdev                  15620  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  3 snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device         14988  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               7097928  38 
pcspkr                 10496  0 
serio_raw              13316  0 
shpchp                 40212  0 
snd                    62628  24 snd_cmipci,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
usblp                  20224  0 
amd64_agp              18184  1 
agpgart                42696  2 nvidia,amd64_agp
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
i2c_nforce2            14980  0 
usbhid                 42336  0 
forcedeth              61712  0 
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
usb_storage            82880  0 
```





I also tried 
```
cd /dev/input
sudo MAKEDEV js
```

Still no dice. I have also tried setting the sidewinder switch at both the one dot and two dot positions. I suppose one of them is supposed to emulate analog mode. Modprobing analog has also not yielded any success. Any help will be greatly appreciated.

Thanks
-sstakes

---

### Post by sstakes1 on 2009-05-03
Looks like all gameport devices are broken in this kernel version. 

I first applied the patch mentioned in this [kernel bug 12426]("http://bugzilla.kernel.org/show_bug.cgi?id=12426").

When I tested it with the patched gameport.ko kernel module, it still did not work. I did some further sleuthing and found that the code that probes for the device in the gameport is never being called (driver::connect() callback method). I'm not very familiar with the kernel or the gameport driver, so I do not know why. I intend to report my findings to the maintainer of the driver. However, I patched the driver to make the call. And voila, the joystick now works! Here is my patch on top of the patch from the kernel bug mentioned above

```
57a58
> static struct gameport* sp_gameport=NULL;
371a373
>                                 printk(KERN_INFO "Received GAMEPORT_REGISTER_PORT\n");
375a378
>                                 printk(KERN_INFO "Received GAMEPORT_ATTACH_DRIVER\n");
558a562,565
> 	printk(KERN_INFO "gameport_add_port:Using patched driver : v1.1\n");
> 	sp_gameport = kmalloc(sizeof(struct gameport), GFP_ATOMIC);
>         memcpy(sp_gameport, gameport, sizeof(struct gameport) );
> 	printk(KERN_INFO "gameport_add_port:adding gameport=%p\n", sp_gameport);
658a666
>         printk(KERN_INFO "__gameport_register_port called\n");
716a725,729
> 
>         if(!sp_gameport && strcmp(drv->driver.name,"joydump")) {
> 		drv->connect(sp_gameport, drv);
> 	}
> 	
723c736
< 
---
>     	printk(KERN_INFO "gameport_register_driver for %s\n", mod_name);
745a759
>     	printk(KERN_INFO "gameport_register_driver enqueing ATTACH_DRIVER\n");
751a766
>     	printk(KERN_INFO "gameport_register_driver exiting\n");
```



There are some caveats though. 

1. The patch above is probably very fragile as it caches a static gameport structure and may not work on systems with multiple gameports.
2. After loading sidewinder module, I have to load and unload the analog module for the joystick to work correctly.
Here is my script to make my joystick to work correctly

```
modprobe joydev
#modprobe joydump
modprobe  snd_cmipci joystick_port=0x201
modprobe  sidewinder
modprobe analog
sleep 3
modprobe -r analog
dmesg
```



I am also attaching my patched kernel module **for those of you who would not mind loading random modules from unverified sources**.

---

### Post by scmaruthi on 2010-02-21
I have the same to devies and am not able to get them to work. Thank you for posting a solution to this, I'm new to linux, so how should I load this kernel module(?). after doing that would the joystick appear as js0 in dev/input/.. I had already done some step suggested in some other discussions to make it appear but doesn't work.. what should i do to restore to orignal.

---

### Post by scmaruthi on 2010-02-21
if I type lsmod I get
```
Module                  Size  Used by
joydump                 3004  0 
sidewinder             11260  0 
snd_opl3_synth         11616  0 
snd_seq_midi_emul       6332  1 snd_opl3_synth
isofs                  31620  0 
udf                    80900  0 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
snd_cmipci             33408  4 
gameport               11368  4 joydump,sidewinder,snd_cmipci
snd_intel8x0           30168  4 
snd_opl3_lib           10396  2 snd_opl3_synth,snd_cmipci
snd_hwdep               7200  1 snd_opl3_lib
snd_mpu401_uart         6940  1 snd_cmipci
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_cmipci,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
iptable_filter          3100  0 
snd_seq                50224  8 snd_opl3_synth,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
joydev                 10240  0 
snd_timer              22276  3 snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device          6920  7 snd_opl3_synth,snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6688  0 
parport_pc             31940  1 
nvidia               8880868  66 
snd                    59204  31 snd_opl3_synth,snd_cmipci,snd_intel8x0,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
intel_agp              27484  1 
agpgart                34988  2 nvidia,intel_agp
```

and when I type dmesg I get
```

[ 1955.682956] VFS: busy inodes on changed media or resized disk sr0
[ 1955.685032] VFS: busy inodes on changed media or resized disk sr0
[ 1955.687130] VFS: busy inodes on changed media or resized disk sr0
[ 1957.719229] VFS: busy inodes on changed media or resized disk sr0
[ 1957.721748] VFS: busy inodes on changed media or resized disk sr0
[ 1957.724040] VFS: busy inodes on changed media or resized disk sr0
[ 1959.683097] VFS: busy inodes on changed media or resized disk sr0
[ 1959.685239] VFS: busy inodes on changed media or resized disk sr0
[ 1959.689288] VFS: busy inodes on changed media or resized disk sr0
[ 1961.682594] VFS: busy inodes on changed media or resized disk sr0
[ 1961.684766] VFS: busy inodes on changed media or resized disk sr0
[ 1961.688980] VFS: busy inodes on changed media or resized disk sr0
[ 1963.682389] VFS: busy inodes on changed media or resized disk sr0
[ 1963.684843] VFS: busy inodes on changed media or resized disk sr0
[ 1963.688851] VFS: busy inodes on changed media or resized disk sr0
[ 1965.682151] VFS: busy inodes on changed media or resized disk sr0
[ 1965.684154] VFS: busy inodes on changed media or resized disk sr0
[ 1965.686326] VFS: busy inodes on changed media or resized disk sr0
[ 1967.683951] VFS: busy inodes on changed media or resized disk sr0
[ 1967.686089] VFS: busy inodes on changed media or resized disk sr0
[ 1967.688054] VFS: busy inodes on changed media or resized disk sr0
[ 1969.688422] VFS: busy inodes on changed media or resized disk sr0
[ 1969.690780] VFS: busy inodes on changed media or resized disk sr0
[ 1969.692924] VFS: busy inodes on changed media or resized disk sr0
[ 1971.682493] VFS: busy inodes on changed media or resized disk sr0
[ 1971.684580] VFS: busy inodes on changed media or resized disk sr0
[ 1971.686864] VFS: busy inodes on changed media or resized disk sr0
[ 1973.686489] VFS: busy inodes on changed media or resized disk sr0
[ 1973.691986] VFS: busy inodes on changed media or resized disk sr0
[ 1973.701797] VFS: busy inodes on changed media or resized disk sr0
[ 1975.682564] VFS: busy inodes on changed media or resized disk sr0
[ 1975.684650] VFS: busy inodes on changed media or resized disk sr0
[ 1975.688117] VFS: busy inodes on changed media or resized disk sr0
[ 1977.682680] VFS: busy inodes on changed media or resized disk sr0
[ 1977.684678] VFS: busy inodes on changed media or resized disk sr0
[ 1977.686855] VFS: busy inodes on changed media or resized disk sr0
[ 1979.683023] VFS: busy inodes on changed media or resized disk sr0
[ 1979.686738] VFS: busy inodes on changed media or resized disk sr0
[ 1979.692794] VFS: busy inodes on changed media or resized disk sr0
[ 1981.683247] VFS: busy inodes on changed media or resized disk sr0
[ 1981.685741] VFS: busy inodes on changed media or resized disk sr0
[ 1981.687959] VFS: busy inodes on changed media or resized disk sr0
[ 1983.699485] VFS: busy inodes on changed media or resized disk sr0
[ 1983.702221] VFS: busy inodes on changed media or resized disk sr0
[ 1983.707156] VFS: busy inodes on changed media or resized disk sr0
[ 1985.682548] VFS: busy inodes on changed media or resized disk sr0
[ 1985.684943] VFS: busy inodes on changed media or resized disk sr0
[ 1985.689033] VFS: busy inodes on changed media or resized disk sr0
[ 1987.683255] VFS: busy inodes on changed media or resized disk sr0
[ 1987.685329] VFS: busy inodes on changed media or resized disk sr0
[ 1987.687422] VFS: busy inodes on changed media or resized disk sr0
[ 1989.682552] VFS: busy inodes on changed media or resized disk sr0
[ 1989.684915] VFS: busy inodes on changed media or resized disk sr0
[ 1989.689031] VFS: busy inodes on changed media or resized disk sr0
[ 1991.683050] VFS: busy inodes on changed media or resized disk sr0
[ 1991.685324] VFS: busy inodes on changed media or resized disk sr0
[ 1991.687418] VFS: busy inodes on changed media or resized disk sr0
[ 1993.682166] VFS: busy inodes on changed media or resized disk sr0
[ 1993.684256] VFS: busy inodes on changed media or resized disk sr0
[ 1993.686406] VFS: busy inodes on changed media or resized disk sr0
[ 1995.688867] VFS: busy inodes on changed media or resized disk sr0
[ 1995.692407] VFS: busy inodes on changed media or resized disk sr0
[ 1995.697186] VFS: busy inodes on changed media or resized disk sr0
[ 1997.689680] VFS: busy inodes on changed media or resized disk sr0
[ 1997.691740] VFS: busy inodes on changed media or resized disk sr0
[ 1997.694487] VFS: busy inodes on changed media or resized disk sr0
[ 1999.682064] VFS: busy inodes on changed media or resized disk sr0
[ 1999.684251] VFS: busy inodes on changed media or resized disk sr0
[ 1999.686432] VFS: busy inodes on changed media or resized disk sr0
[ 2012.907140] CPU0 attaching NULL sched-domain.
[ 2012.907150] CPU1 attaching NULL sched-domain.
[ 2012.916096] CPU0 attaching sched-domain:
[ 2012.916101]  domain 0: span 0-1 level SIBLING
[ 2012.916106]   groups: 0 1
[ 2012.916115] CPU1 attaching sched-domain:
[ 2012.916119]  domain 0: span 0-1 level SIBLING
[ 2012.916122]   groups: 1 0
[ 2014.553765] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[ 2014.553779] PM: Basic memory bitmaps created
[ 2014.553783] PM: Syncing filesystems ... done.
[ 2014.633924] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 2014.635739] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 2014.635901] PM: Shrinking memory... done (69977 pages freed)
[ 2015.420082] PM: Freed 279908 kbytes in 0.78 seconds (358.85 MB/s)
[ 2015.420086] Suspending console(s) (use no_console_suspend to debug)
[ 2015.422247] sd 1:0:0:0: [sda] Synchronizing SCSI cache
[ 2015.423161] parport_pc 00:06: disabled
[ 2015.423414] serial 00:05: disabled
[ 2015.423505] C-Media PCI 0000:01:0b.0: PCI INT A disabled
[ 2015.831668] Intel ICH 0000:00:1f.5: PCI INT B disabled
[ 2015.831867] ata_piix 0000:00:1f.2: PCI INT A disabled
[ 2015.831976] ata_piix 0000:00:1f.1: PCI INT A disabled
[ 2015.832559] ACPI: Preparing to enter system sleep state S4
[ 2015.833097] PM: Saving platform NVS memory
[ 2015.833617] Disabling non-boot CPUs ...
[ 2015.936022] CPU 1 is now offline
[ 2015.936027] SMP alternatives: switching to UP code
[ 2015.944251] CPU0 attaching NULL sched-domain.
[ 2015.944257] CPU1 attaching NULL sched-domain.
[ 2015.944266] CPU0 attaching NULL sched-domain.
[ 2015.944553] CPU1 is down
[ 2015.944658] PM: Creating hibernation image: 
[ 2015.948007] PM: Need to copy 121838 pages
[ 2015.948007] PM: Normal pages needed: 112407 + 1024 + 24, available pages: 128696
[ 2015.948007] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 2015.948007] PM: Restoring platform NVS memory
[ 2015.948007] CPU0: Thermal LVT vector (0xfa) already installed
[ 2015.948007] Force enabled HPET at resume
[ 2015.948007] Enabling non-boot CPUs ...
[ 2015.948007] SMP alternatives: switching to SMP code
[ 2015.952657] Booting processor 1 APIC 0x1 ip 0x6000
[ 2015.944018] Initializing CPU#1
[ 2015.944018] Calibrating delay using timer specific routine.. 5599.69 BogoMIPS (lpj=11199399)
[ 2015.944018] CPU: Trace cache: 12K uops, L1 D cache: 8K
[ 2015.944018] CPU: L2 cache: 512K
[ 2015.944018] CPU: Physical Processor ID: 0
[ 2015.944018] CPU: Processor Core ID: 0
[ 2015.944018] mce: CPU supports 4 MCE banks
[ 2015.944018] CPU1: Thermal monitoring enabled (TM1)
[ 2015.944018] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[ 2016.040839] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[ 2016.040860] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[ 2016.061018] Switched to high resolution mode on CPU 1
[ 2016.061022] CPU0 attaching NULL sched-domain.
[ 2016.076021] CPU0 attaching sched-domain:
[ 2016.076026]  domain 0: span 0-1 level SIBLING
[ 2016.076029]   groups: 0 1
[ 2016.076036] CPU1 attaching sched-domain:
[ 2016.076038]  domain 0: span 0-1 level SIBLING
[ 2016.076041]   groups: 1 0
[ 2016.077019] CPU1 is up
[ 2016.077039] ACPI: Waking up from system sleep state S4
[ 2016.077652] agpgart-intel 0000:00:00.0: restoring config space at offset 0x1 (was 0x20900006, writing 0x30900006)
[ 2016.077849] ehci_hcd 0000:00:1d.7: PME# disabled
[ 2016.077866] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x2280b0b0, writing 0x3280b0b0)
[ 2016.077878] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x800107, writing 0x8800107)
[ 2016.077931] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2880003, writing 0x2880007)
[ 2016.077956] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2a00001, writing 0x2a00005)
[ 2016.078008] Intel ICH 0000:00:1f.5: restoring config space at offset 0x1 (was 0x2900007, writing 0x2900003)
[ 2016.078035] nvidia 0000:01:00.0: restoring config space at offset 0xc (was 0xfe5e0000, writing 0x0)
[ 2016.078053] nvidia 0000:01:00.0: restoring config space at offset 0x3 (was 0x2000, writing 0xf800)
[ 2016.078101] C-Media PCI 0000:01:0b.0: restoring config space at offset 0x1 (was 0x2000005, writing 0x2000001)
[ 2016.085776] pci 0000:00:02.0: PME# disabled
[ 2016.085792] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 2016.085823] usb usb2: root hub lost power or was reset
[ 2016.085874] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 2016.085903] usb usb3: root hub lost power or was reset
[ 2016.085920] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 2016.085948] usb usb4: root hub lost power or was reset
[ 2016.085964] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 2016.085992] usb usb5: root hub lost power or was reset
[ 2016.086009] ehci_hcd 0000:00:1d.7: PME# disabled
[ 2016.086014] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 2016.086020] usb usb1: root hub lost power or was reset
[ 2016.089916] ehci_hcd 0000:00:1d.7: debug port 1
[ 2016.089923] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[ 2016.089969] pci 0000:00:1e.0: setting latency timer to 64
[ 2016.089988] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2016.089994] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 2016.090058] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2016.090065] ata_piix 0000:00:1f.2: setting latency timer to 64
[ 2016.090178] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 2016.090187] Intel ICH 0000:00:1f.5: setting latency timer to 64
[ 2016.272891] ata2.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[ 2016.272893] C-Media PCI 0000:01:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 2016.272906] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[ 2016.273319] ata2.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded
[ 2016.274244] serial 00:05: activated
[ 2016.275667] parport_pc 00:06: activated
[ 2016.280558] ata3.00: configured for UDMA/100
[ 2016.297352] ata2.00: configured for UDMA/100
[ 2016.321366] ata2.00: configured for UDMA/100
[ 2016.321370] ata2: EH complete
[ 2016.772281] sd 1:0:0:0: [sda] Starting disk
[ 2017.048024] usb 2-2: reset low speed USB device using uhci_hcd and address 2
[ 2017.356135] PM: Image restored successfully.
[ 2017.414620] Restarting tasks ... done.
[ 2017.415105] PM: Basic memory bitmaps freed
[ 2018.154427] eth0: link down
[ 2018.154721] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2019.585218] CPU0 attaching NULL sched-domain.
[ 2019.585228] CPU1 attaching NULL sched-domain.
[ 2019.604198] CPU0 attaching sched-domain:
[ 2019.604207]  domain 0: span 0-1 level SIBLING
[ 2019.604213]   groups: 0 1
[ 2019.604223]   domain 1: span 0-1 level MC
[ 2019.604228]    groups: 0-1 (__cpu_power = 2048)
[ 2019.604241] CPU1 attaching sched-domain:
[ 2019.604246]  domain 0: span 0-1 level SIBLING
[ 2019.604251]   groups: 1 0
[ 2019.604259]   domain 1: span 0-1 level MC
[ 2019.604264]    groups: 0-1 (__cpu_power = 2048)
[ 3119.553913] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 3119.554072] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3129.984012] eth0: no IPv6 routers present
[ 3155.429223] eth0: link down
[ 3156.985978] eth0: link up, 100Mbps, full-duplex, lpa 0xC1E1
[ 3651.239870] CPU0 attaching NULL sched-domain.
[ 3651.239880] CPU1 attaching NULL sched-domain.
[ 3651.256101] CPU0 attaching sched-domain:
[ 3651.256107]  domain 0: span 0-1 level SIBLING
[ 3651.256112]   groups: 0 1
[ 3651.256122] CPU1 attaching sched-domain:
[ 3651.256125]  domain 0: span 0-1 level SIBLING
[ 3651.256129]   groups: 1 0
[ 3653.011820] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[ 3653.011830] PM: Basic memory bitmaps created
[ 3653.011833] PM: Syncing filesystems ... done.
[ 3653.021084] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 3653.022547] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 3653.022703] PM: Shrinking memory... done (13281 pages freed)
[ 3653.246012] PM: Freed 53124 kbytes in 0.22 seconds (241.47 MB/s)
[ 3653.246017] Suspending console(s) (use no_console_suspend to debug)
[ 3653.247552] sd 1:0:0:0: [sda] Synchronizing SCSI cache
[ 3653.248487] parport_pc 00:06: disabled
[ 3653.248743] serial 00:05: disabled
[ 3653.248834] C-Media PCI 0000:01:0b.0: PCI INT A disabled
[ 3653.656034] Intel ICH 0000:00:1f.5: PCI INT B disabled
[ 3653.656209] ata_piix 0000:00:1f.2: PCI INT A disabled
[ 3653.656317] ata_piix 0000:00:1f.1: PCI INT A disabled
[ 3653.656895] ACPI: Preparing to enter system sleep state S4
[ 3653.657422] PM: Saving platform NVS memory
[ 3653.657903] Disabling non-boot CPUs ...
[ 3653.760019] CPU 1 is now offline
[ 3653.760024] SMP alternatives: switching to UP code
[ 3653.768257] CPU0 attaching NULL sched-domain.
[ 3653.768263] CPU1 attaching NULL sched-domain.
[ 3653.768272] CPU0 attaching NULL sched-domain.
[ 3653.768566] CPU1 is down
[ 3653.768671] PM: Creating hibernation image: 
[ 3653.772007] PM: Need to copy 126526 pages
[ 3653.772007] PM: Normal pages needed: 125733 + 1024 + 24, available pages: 132647
[ 3653.772007] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 3653.772007] PM: Restoring platform NVS memory
[ 3653.772007] CPU0: Thermal LVT vector (0xfa) already installed
[ 3653.772007] Force enabled HPET at resume
[ 3653.772007] Enabling non-boot CPUs ...
[ 3653.772007] SMP alternatives: switching to SMP code
[ 3653.776661] Booting processor 1 APIC 0x1 ip 0x6000
[ 3653.768015] Initializing CPU#1
[ 3653.768015] Calibrating delay using timer specific routine.. 5600.07 BogoMIPS (lpj=11200157)
[ 3653.768015] CPU: Trace cache: 12K uops, L1 D cache: 8K
[ 3653.768015] CPU: L2 cache: 512K
[ 3653.768015] CPU: Physical Processor ID: 0
[ 3653.768015] CPU: Processor Core ID: 0
[ 3653.768015] mce: CPU supports 4 MCE banks
[ 3653.768015] CPU1: Thermal monitoring enabled (TM1)
[ 3653.768015] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[ 3653.864837] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[ 3653.864858] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[ 3653.884998] CPU0 attaching NULL sched-domain.
[ 3653.888020] Switched to high resolution mode on CPU 1
[ 3653.894152] CPU0 attaching sched-domain:
[ 3653.894159]  domain 0: span 0-1 level SIBLING
[ 3653.894163]   groups: 0 1
[ 3653.894172] CPU1 attaching sched-domain:
[ 3653.894175]  domain 0: span 0-1 level SIBLING
[ 3653.894178]   groups: 1 0
[ 3653.897027] CPU1 is up
[ 3653.897048] ACPI: Waking up from system sleep state S4
[ 3653.897681] agpgart-intel 0000:00:00.0: restoring config space at offset 0x1 (was 0x20900006, writing 0x30900006)
[ 3653.897879] ehci_hcd 0000:00:1d.7: PME# disabled
[ 3653.897896] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x2280b0b0, writing 0x3280b0b0)
[ 3653.897909] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x800107, writing 0x8800107)
[ 3653.897961] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2880003, writing 0x2880007)
[ 3653.897986] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2a00001, writing 0x2a00005)
[ 3653.898038] Intel ICH 0000:00:1f.5: restoring config space at offset 0x1 (was 0x2900007, writing 0x2900003)
[ 3653.898066] nvidia 0000:01:00.0: restoring config space at offset 0xc (was 0xfe5e0000, writing 0x0)
[ 3653.898084] nvidia 0000:01:00.0: restoring config space at offset 0x3 (was 0x2000, writing 0xf800)
[ 3653.898132] C-Media PCI 0000:01:0b.0: restoring config space at offset 0x1 (was 0x2000005, writing 0x2000001)
[ 3653.905850] pci 0000:00:02.0: PME# disabled
[ 3653.905866] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 3653.905897] usb usb2: root hub lost power or was reset
[ 3653.905948] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 3653.905977] usb usb3: root hub lost power or was reset
[ 3653.905993] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 3653.906021] usb usb4: root hub lost power or was reset
[ 3653.906038] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 3653.906065] usb usb5: root hub lost power or was reset
[ 3653.906083] ehci_hcd 0000:00:1d.7: PME# disabled
[ 3653.906088] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 3653.906094] usb usb1: root hub lost power or was reset
[ 3653.909985] ehci_hcd 0000:00:1d.7: debug port 1
[ 3653.909993] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[ 3653.910037] pci 0000:00:1e.0: setting latency timer to 64
[ 3653.910056] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 3653.910061] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 3653.910126] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 3653.910134] ata_piix 0000:00:1f.2: setting latency timer to 64
[ 3653.910247] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 3653.910256] Intel ICH 0000:00:1f.5: setting latency timer to 64
[ 3654.092420] ata2.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[ 3654.092427] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[ 3654.092940] ata2.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded
[ 3654.095022] C-Media PCI 0000:01:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 3654.096297] serial 00:05: activated
[ 3654.097743] parport_pc 00:06: activated
[ 3654.100567] ata3.00: configured for UDMA/100
[ 3654.117341] ata2.00: configured for UDMA/100
[ 3654.141340] ata2.00: configured for UDMA/100
[ 3654.141344] ata2: EH complete
[ 3654.596281] sd 1:0:0:0: [sda] Starting disk
[ 3654.876015] usb 2-2: reset low speed USB device using uhci_hcd and address 2
[ 3655.184135] PM: Image restored successfully.
[ 3655.242979] Restarting tasks ... done.
[ 3655.243456] PM: Basic memory bitmaps freed
[ 3655.870922] eth0: link up, 100Mbps, full-duplex, lpa 0xC1E1
[ 3656.866376] CPU0 attaching NULL sched-domain.
[ 3656.866386] CPU1 attaching NULL sched-domain.
[ 3656.885089] CPU0 attaching sched-domain:
[ 3656.885095]  domain 0: span 0-1 level SIBLING
[ 3656.885100]   groups: 0 1
[ 3656.885107]   domain 1: span 0-1 level MC
[ 3656.885111]    groups: 0-1 (__cpu_power = 2048)
[ 3656.885120] CPU1 attaching sched-domain:
[ 3656.885123]  domain 0: span 0-1 level SIBLING
[ 3656.885127]   groups: 1 0
[ 3656.885134]   domain 1: span 0-1 level MC
[ 3656.885137]    groups: 0-1 (__cpu_power = 2048)
[ 4921.151806] UDF-fs: Partition marked readonly; forcing readonly mount
[ 4921.179185] UDF-fs INFO UDF: Mounting volume 'Nero-NE8360', timestamp 2009/04/02 14:24 (114a)
[ 5429.915295] eth0: link down
[ 5449.763066] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 5451.467222] eth0: link down
[ 5453.065896] eth0: link up, 100Mbps, full-duplex, lpa 0xC1E1
[ 5468.117590] VFS: busy inodes on changed media or resized disk sr0
[ 5468.124730] VFS: busy inodes on changed media or resized disk sr0
[ 5468.133775] VFS: busy inodes on changed media or resized disk sr0
[ 5468.139010] VFS: busy inodes on changed media or resized disk sr0
[ 5468.184801] VFS: busy inodes on changed media or resized disk sr0
[ 5468.192061] VFS: busy inodes on changed media or resized disk sr0
[ 5469.114726] VFS: busy inodes on changed media or resized disk sr0
[ 5469.117179] VFS: busy inodes on changed media or resized disk sr0
[ 5469.166889] VFS: busy inodes on changed media or resized disk sr0
[ 5469.169112] VFS: busy inodes on changed media or resized disk sr0
[ 5469.174960] VFS: busy inodes on changed media or resized disk sr0
[ 5469.178899] VFS: busy inodes on changed media or resized disk sr0
[ 5470.114478] VFS: busy inodes on changed media or resized disk sr0
[ 5471.119659] VFS: busy inodes on changed media or resized disk sr0
[ 5471.124333] VFS: busy inodes on changed media or resized disk sr0
[ 5472.112647] VFS: busy inodes on changed media or resized disk sr0
[ 5473.114122] VFS: busy inodes on changed media or resized disk sr0
[ 5473.118071] VFS: busy inodes on changed media or resized disk sr0
[ 5474.155371] VFS: busy inodes on changed media or resized disk sr0
[ 5475.136507] VFS: busy inodes on changed media or resized disk sr0
[ 5475.140530] VFS: busy inodes on changed media or resized disk sr0
[ 5476.112060] VFS: busy inodes on changed media or resized disk sr0
[ 5477.468444] VFS: busy inodes on changed media or resized disk sr0
[ 5477.472499] VFS: busy inodes on changed media or resized disk sr0
[ 5478.113874] VFS: busy inodes on changed media or resized disk sr0
[ 5479.111746] VFS: busy inodes on changed media or resized disk sr0
[ 5479.113949] VFS: busy inodes on changed media or resized disk sr0
[ 5480.113014] VFS: busy inodes on changed media or resized disk sr0
[ 5481.112491] VFS: busy inodes on changed media or resized disk sr0
[ 5481.114551] VFS: busy inodes on changed media or resized disk sr0
[ 5482.112132] VFS: busy inodes on changed media or resized disk sr0
[ 5483.112064] VFS: busy inodes on changed media or resized disk sr0
[ 5483.114283] VFS: busy inodes on changed media or resized disk sr0
[ 5484.112226] VFS: busy inodes on changed media or resized disk sr0
[ 5485.112854] VFS: busy inodes on changed media or resized disk sr0
[ 5485.114979] VFS: busy inodes on changed media or resized disk sr0
[ 5486.110645] VFS: busy inodes on changed media or resized disk sr0
[ 5487.112446] VFS: busy inodes on changed media or resized disk sr0
[ 5487.114569] VFS: busy inodes on changed media or resized disk sr0
[ 5488.112718] VFS: busy inodes on changed media or resized disk sr0
[ 5489.112165] VFS: busy inodes on changed media or resized disk sr0
[ 5489.114290] VFS: busy inodes on changed media or resized disk sr0
[ 5490.112923] VFS: busy inodes on changed media or resized disk sr0
[ 5491.112733] VFS: busy inodes on changed media or resized disk sr0
[ 5491.114817] VFS: busy inodes on changed media or resized disk sr0
[ 5492.112080] VFS: busy inodes on changed media or resized disk sr0
[ 5493.112408] VFS: busy inodes on changed media or resized disk sr0
[ 5493.114478] VFS: busy inodes on changed media or resized disk sr0
[ 5494.112236] VFS: busy inodes on changed media or resized disk sr0
[ 5495.113112] VFS: busy inodes on changed media or resized disk sr0
[ 5495.115238] VFS: busy inodes on changed media or resized disk sr0
[ 5496.112348] VFS: busy inodes on changed media or resized disk sr0
[ 5497.112832] VFS: busy inodes on changed media or resized disk sr0
[ 5497.114897] VFS: busy inodes on changed media or resized disk sr0
[ 5498.112533] VFS: busy inodes on changed media or resized disk sr0
[ 5499.112475] VFS: busy inodes on changed media or resized disk sr0
[ 5499.114627] VFS: busy inodes on changed media or resized disk sr0
[ 5500.111598] VFS: busy inodes on changed media or resized disk sr0
[ 5501.112129] VFS: busy inodes on changed media or resized disk sr0
[ 5501.114342] VFS: busy inodes on changed media or resized disk sr0
[ 5502.112679] VFS: busy inodes on changed media or resized disk sr0
[ 5503.113918] VFS: busy inodes on changed media or resized disk sr0
[ 5503.117415] VFS: busy inodes on changed media or resized disk sr0
[ 5504.112896] VFS: busy inodes on changed media or resized disk sr0
[ 5505.113767] VFS: busy inodes on changed media or resized disk sr0
[ 5505.121662] VFS: busy inodes on changed media or resized disk sr0
[ 5506.113044] VFS: busy inodes on changed media or resized disk sr0
[ 5507.112915] VFS: busy inodes on changed media or resized disk sr0
[ 5507.115132] VFS: busy inodes on changed media or resized disk sr0
[ 5508.112235] VFS: busy inodes on changed media or resized disk sr0
[ 5509.112627] VFS: busy inodes on changed media or resized disk sr0
[ 5509.114779] VFS: busy inodes on changed media or resized disk sr0
[ 5510.112346] VFS: busy inodes on changed media or resized disk sr0
[ 5511.112569] VFS: busy inodes on changed media or resized disk sr0
[ 5511.114630] VFS: busy inodes on changed media or resized disk sr0
[ 5512.112449] VFS: busy inodes on changed media or resized disk sr0
[ 5513.112478] VFS: busy inodes on changed media or resized disk sr0
[ 5513.114676] VFS: busy inodes on changed media or resized disk sr0
[ 5514.112965] VFS: busy inodes on changed media or resized disk sr0
[ 5515.112030] VFS: busy inodes on changed media or resized disk sr0
[ 5515.114132] VFS: busy inodes on changed media or resized disk sr0
[ 5516.112100] VFS: busy inodes on changed media or resized disk sr0
[ 5517.112629] VFS: busy inodes on changed media or resized disk sr0
[ 5517.114798] VFS: busy inodes on changed media or resized disk sr0
[ 5518.112212] VFS: busy inodes on changed media or resized disk sr0
[ 5519.112381] VFS: busy inodes on changed media or resized disk sr0
[ 5519.114578] VFS: busy inodes on changed media or resized disk sr0
[ 5520.113127] VFS: busy inodes on changed media or resized disk sr0
[ 5521.176340] VFS: busy inodes on changed media or resized disk sr0
[ 5521.206315] VFS: busy inodes on changed media or resized disk sr0
[ 5522.112571] VFS: busy inodes on changed media or resized disk sr0
[ 5523.112191] VFS: busy inodes on changed media or resized disk sr0
[ 5523.114317] VFS: busy inodes on changed media or resized disk sr0
[ 5524.112677] VFS: busy inodes on changed media or resized disk sr0
[ 5525.112828] VFS: busy inodes on changed media or resized disk sr0
[ 5525.115036] VFS: busy inodes on changed media or resized disk sr0
[ 5526.112786] VFS: busy inodes on changed media or resized disk sr0
[ 5527.112622] VFS: busy inodes on changed media or resized disk sr0
[ 5527.114697] VFS: busy inodes on changed media or resized disk sr0
[ 5528.112957] VFS: busy inodes on changed media or resized disk sr0
[ 5529.112758] VFS: busy inodes on changed media or resized disk sr0
[ 5529.115277] VFS: busy inodes on changed media or resized disk sr0
[ 5530.111007] VFS: busy inodes on changed media or resized disk sr0
[ 5531.112241] VFS: busy inodes on changed media or resized disk sr0
[ 5531.114322] VFS: busy inodes on changed media or resized disk sr0
[ 5532.112231] VFS: busy inodes on changed media or resized disk sr0
[ 5533.110872] VFS: busy inodes on changed media or resized disk sr0
[ 5533.113125] VFS: busy inodes on changed media or resized disk sr0
[ 5534.112331] VFS: busy inodes on changed media or resized disk sr0
[ 5535.112830] VFS: busy inodes on changed media or resized disk sr0
[ 5535.115020] VFS: busy inodes on changed media or resized disk sr0
[ 5536.112247] VFS: busy inodes on changed media or resized disk sr0
[ 5537.112534] VFS: busy inodes on changed media or resized disk sr0
[ 5537.114594] VFS: busy inodes on changed media or resized disk sr0
[ 5538.112344] VFS: busy inodes on changed media or resized disk sr0
[ 5539.112647] VFS: busy inodes on changed media or resized disk sr0
[ 5539.114775] VFS: busy inodes on changed media or resized disk sr0
[ 5540.112419] VFS: busy inodes on changed media or resized disk sr0
[ 5541.116982] VFS: busy inodes on changed media or resized disk sr0
[ 5541.120398] VFS: busy inodes on changed media or resized disk sr0
[ 5542.112950] VFS: busy inodes on changed media or resized disk sr0
[ 5543.111961] VFS: busy inodes on changed media or resized disk sr0
[ 5543.114244] VFS: busy inodes on changed media or resized disk sr0
[ 5544.111073] VFS: busy inodes on changed media or resized disk sr0
[ 5545.112810] VFS: busy inodes on changed media or resized disk sr0
[ 5545.115076] VFS: busy inodes on changed media or resized disk sr0
[ 5546.112817] VFS: busy inodes on changed media or resized disk sr0
[ 5547.112793] VFS: busy inodes on changed media or resized disk sr0
[ 5547.114919] VFS: busy inodes on changed media or resized disk sr0
[ 5548.112942] VFS: busy inodes on changed media or resized disk sr0
[ 5549.112133] VFS: busy inodes on changed media or resized disk sr0
[ 5549.114332] VFS: busy inodes on changed media or resized disk sr0
[ 5550.110893] VFS: busy inodes on changed media or resized disk sr0
[ 5551.111784] VFS: busy inodes on changed media or resized disk sr0
[ 5551.114594] VFS: busy inodes on changed media or resized disk sr0
[ 5552.112976] VFS: busy inodes on changed media or resized disk sr0
[ 5553.112500] VFS: busy inodes on changed media or resized disk sr0
[ 5553.114975] VFS: busy inodes on changed media or resized disk sr0
[ 5554.112067] VFS: busy inodes on changed media or resized disk sr0
[ 5555.112879] VFS: busy inodes on changed media or resized disk sr0
[ 5555.115009] VFS: busy inodes on changed media or resized disk sr0
[ 5556.112371] VFS: busy inodes on changed media or resized disk sr0
[ 5557.112997] VFS: busy inodes on changed media or resized disk sr0
[ 5557.115210] VFS: busy inodes on changed media or resized disk sr0
[ 5558.112503] VFS: busy inodes on changed media or resized disk sr0
[ 5559.112591] VFS: busy inodes on changed media or resized disk sr0
[ 5559.114738] VFS: busy inodes on changed media or resized disk sr0
[ 7269.969731] eth0: link down
[ 7282.644530] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 7283.972899] eth0: link down
[ 7285.580367] eth0: link up, 100Mbps, full-duplex, lpa 0xC1E1
[ 9145.682984] eth0: link down
[ 9158.320271] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 9159.714418] eth0: link down
[ 9161.256156] eth0: link up, 100Mbps, full-duplex, lpa 0xC1E1
[ 9561.773075] eth0: link down
[11845.830397] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[11847.598718] eth0: link down
[11849.185650] eth0: link up, 100Mbps, full-duplex, lpa 0xC1E1
[12866.928531] joydump: ,------------------ START ----------------.
[12866.928538] joydump: | Dumping:      pci0000:01:0b.0/gameport0 |
[12866.928542] joydump: | Speed:                         1420 kHz |
[12866.939183] joydump: >------------------ DATA -----------------<
[12866.939199] joydump: | index:   0 delta:   0 us data: 11111111 |
[12866.939233] joydump: `------------------- END -----------------'

```Is my gameport recognised? Comparing with your post above, it seems mine is not setup correctly..Please help..

---

### Post by Scot_Bernard on 2010-10-09
> **sstakes1 said:**
> Looks like all gameport devices are broken in this kernel version. 

I first applied the patch mentioned in this [kernel bug 12426]("http://bugzilla.kernel.org/show_bug.cgi?id=12426").

When I tested it with the patched gameport.ko kernel module, it still did not work. I did some further sleuthing and found that the code that probes for the device in the gameport is never being called (driver::connect() callback method). I'm not very familiar with the kernel or the gameport driver, so I do not know why. I intend to report my findings to the maintainer of the driver. However, I patched the driver to make the call. And voila, the joystick now works! Here is my patch on top of the patch from the kernel bug mentioned above

```
57a58
> static struct gameport* sp_gameport=NULL;
371a373
>                                 printk(KERN_INFO "Received GAMEPORT_REGISTER_PORT\n");
375a378
>                                 printk(KERN_INFO "Received GAMEPORT_ATTACH_DRIVER\n");
558a562,565
> 	printk(KERN_INFO "gameport_add_port:Using patched driver : v1.1\n");
> 	sp_gameport = kmalloc(sizeof(struct gameport), GFP_ATOMIC);
>         memcpy(sp_gameport, gameport, sizeof(struct gameport) );
> 	printk(KERN_INFO "gameport_add_port:adding gameport=%p\n", sp_gameport);
658a666
>         printk(KERN_INFO "__gameport_register_port called\n");
716a725,729
> 
>         if(!sp_gameport && strcmp(drv->driver.name,"joydump")) {
> 		drv->connect(sp_gameport, drv);
> 	}
> 	
723c736
< 
---
>     	printk(KERN_INFO "gameport_register_driver for %s\n", mod_name);
745a759
>     	printk(KERN_INFO "gameport_register_driver enqueing ATTACH_DRIVER\n");
751a766
>     	printk(KERN_INFO "gameport_register_driver exiting\n");
```



There are some caveats though. 

1. The patch above is probably very fragile as it caches a static gameport structure and may not work on systems with multiple gameports.
2. After loading sidewinder module, I have to load and unload the analog module for the joystick to work correctly.
Here is my script to make my joystick to work correctly

```
modprobe joydev
#modprobe joydump
modprobe  snd_cmipci joystick_port=0x201
modprobe  sidewinder
modprobe analog
sleep 3
modprobe -r analog
dmesg
```



I am also attaching my patched kernel module **for those of you who would not mind loading random modules from unverified sources**.

I've tried blacklisting modules and loading them in the exact order you mention, but i don't get the /dev/input/js* node created. I'm using Ubuntu 10.04 64 bits, you still have your joystick working?

---

