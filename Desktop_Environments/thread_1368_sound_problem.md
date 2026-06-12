---
title: "sound problem"
date: 2004-10-20
forum: Desktop Environments
---

### Post by haha on 2004-10-20
I want to sound.

problem :
   I upgraded Ubuntu Linux 4.10.
   when i met first gdm, I can hear welcome sound(?)
   but after i logined in my account/pass, I cannot use sound.
   how can i configured my sound setting??

my lsmod : 
> root@ubuntu:~ # lsmod
Module                  Size  Used by
sis                    51968  2
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ds                     17796  2
ipv6                  230020  8
af_packet              20872  2
ohci1394               32004  0
yenta_socket           19328  0
pcmcia_core            63156  2 ds,yenta_socket
pci_hotplug            30640  0
snd_trident            42920  0
snd_ac97_codec         59268  1 snd_trident
snd_pcm_oss            48168  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  2 snd_trident,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  2 snd_trident,snd_pcm
gameport                4736  1 snd_trident
snd_util_mem            4608  1 snd_trident
snd_mpu401_uart         7296  1 snd_trident
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  2 snd_trident,snd_rawmidi
snd                    50660  10 snd_trident,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_util_mem,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  1 snd
ohci_hcd               19460  0
usbcore               104292  3 ohci_hcd
sis900                 18436  0
crc32                   4608  1 sis900
sis_agp                 8068  1
agpgart                31784  2 sis_agp
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  0
lp                     10436  0
parport                37320  2 parport_pc,lp
sbp2                   22408  0
ieee1394              100536  2 ohci1394,sbp2
tsdev                   7168  0
joydev                  9536  0
evdev                   9088  1
ide_cd                 38276  0
mousedev               10124  1
psmouse                17800  0
sr_mod                 15780  0
scsi_mod              115148  2 sbp2,sr_mod
cdrom                  35872  2 ide_cd,sr_mod
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
sis5513                15240  1
ide_disk               16768  2
ide_core              125272  4 ide_cd,ide_generic,sis5513,ide_disk
unix                   25904  724
fbcon                  27556  71
font                    8576  1 fbcon
vesafb                  6688  1
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb


my dmesg :
> 
root@ubuntu:~ # cat /var/log/dmesg
Linux version 2.6.8.1-3-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 12:41:57 BST 2004
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000015ff0000 (usable)
 BIOS-e820: 0000000015ff0000 - 0000000015ff8000 (ACPI data)
 BIOS-e820: 0000000015ff8000 - 0000000016000000 (ACPI NVS)
 BIOS-e820: 00000000ffef0000 - 00000000fff00000 (reserved)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
351MB LOWMEM available.
On node 0 totalpages: 90096
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 86000 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI disabled because your bios is from 97                         and too old
You can enable it with acpi=force
Built 1 zonelists
Kernel command line: root=/dev/hda4 vga=771 pci=noapic ro quiet splash
PCI: Unknown option `noapic'
Local APIC disabled by BIOS -- reenabling.
Could not enable APIC!
Initializing CPU#0
PID hash table entries: 2048 (order 11: 16384 bytes)
Detected 1333.754 MHz processor.
Using tsc for high-res timesource
Console: colour dummy device 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 349692k/360384k available (1336k kernel code, 9904k reserved, 728k data, 204k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 2646.01 BogoMIPS
Security Scaffold v1.0.0 initialized
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000
CPU: After vendor identify, caps:  0383f9ff 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 256K
CPU: After all inits, caps:        0383f9ff 00000000 00000000 00000040
CPU: Intel Mobile Intel(R) Celeron(TM) CPU         1333MHz stepping 04
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Freeing initrd memory: 4136k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfdb61, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20040816
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00f87a0
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x7804, dseg 0xf0000
PnPBIOS: 11 nodes reported by PnP BIOS; 11 recorded by driver
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
Uncovering SIS18 that hid as a SIS503 (compatible=0)
Enabling SiS 96x SMBus.
PCI: Using IRQ router SIS [1039/0018] at 0000:00:01.0
PCI: IRQ 0 for device 0000:00:03.0 doesn't match PIRQ mask - try pci=usepirqmaskPCI: Found IRQ 11 for device 0000:00:03.0
PCI: Sharing IRQ 11 with 0000:00:01.1
PCI: Sharing IRQ 11 with 0000:00:01.6
PCI: Sharing IRQ 11 with 0000:00:0a.0
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug &amp; Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
PCI: Found IRQ 11 for device 0000:00:01.6
PCI: Sharing IRQ 11 with 0000:00:01.1
PCI: Sharing IRQ 11 with 0000:00:03.0
PCI: Sharing IRQ 11 with 0000:00:0a.0
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4136 blocks [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 204k freed
vesafb: framebuffer at 0xd0000000, mapped to 0xd681c000, size 937k
vesafb: mode is 800x600x8, linelength=800, pages=15
vesafb: protected mode interface info at caaa:0004
vesafb: scrolling: redraw
fb0: VESA VGA frame buffer device
Console: switching to colour frame buffer device 100x37
thermal: Unknown symbol acpi_processor_set_thermal_limit
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
SIS5513: IDE controller at PCI slot 0000:00:00.1
SIS5513: chipset revision 208
SIS5513: not 100% native mode: will probe irqs later
SIS5513: SiS630 ATA 100 (1st gen) controller
    ide0: BM-DMA at 0x7ee0-0x7ee7, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0x7ee8-0x7eef, BIOS settings: hdc:DMA, hdd:DMA
hda: FUJITSU MHS2020AT E, ATA DISK drive
Using anticipatory io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 39070080 sectors (20003 MB) w/2048KiB Cache, CHS=38760/16/63, UDMA(100)
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4
hdc: QSI CD-ROM SCR-242, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
EXT3 FS on hda4, internal journal
SCSI subsystem initialized
Synaptics Touchpad, model: 1
 Firmware: 5.1
 180 degree mounted touchpad
 Sensor: 15
 new absolute packet format
 Touchpad has extended capability bits
 -&gt; four buttons
 -&gt; multifinger detection
 -&gt; palm detection
input: SynPS/2 Synaptics TouchPad on isa0060/serio1
mice: PS/2 mouse device common for all mice
hdc: ATAPI 24X CD-ROM drive, 128kB Cache, UDMA(33)
Uniform CD-ROM driver Revision: 3.20
ts: Compaq touchscreen protocol output
ieee1394: Initialized config rom entry `ip1394'
sbp2: $Rev: 1219 $ Ben Collins &lt;bcollins@debian.org&gt;
lp: driver loaded but no devices found
Capability LSM initialized
device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected SiS 630 chipset
agpgart: Maximum main memory to use for agp memory: 291M
agpgart: AGP aperture is 64M @ 0xe0000000
sis900.c: v1.08.07 11/02/2003
PCI: Found IRQ 11 for device 0000:00:01.1
PCI: Sharing IRQ 11 with 0000:00:01.6
PCI: Sharing IRQ 11 with 0000:00:03.0
PCI: Sharing IRQ 11 with 0000:00:0a.0
eth0: ICS LAN PHY transceiver found at address 1.
eth0: Using transceiver found at address 1 as default
eth0: SiS 900 PCI Fast Ethernet at 0xd000, IRQ 11, 00:40:45:11:45:bc.
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Feb 02 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ohci_hcd: block sizes: ed 64 td 64
PCI: Found IRQ 10 for device 0000:00:01.2
PCI: Sharing IRQ 10 with 0000:00:01.3
ohci_hcd 0000:00:01.2: Silicon Integrated Systems [SiS] USB 1.0 Controller
ohci_hcd 0000:00:01.2: irq 10, pci mem d6a27000
ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
PCI: Found IRQ 10 for device 0000:00:01.3
PCI: Sharing IRQ 10 with 0000:00:01.2
ohci_hcd 0000:00:01.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
ohci_hcd 0000:00:01.3: irq 10, pci mem d6a29000
ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
PCI: Found IRQ 5 for device 0000:00:01.4
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: Found IRQ 11 for device 0000:00:03.0
PCI: Sharing IRQ 11 with 0000:00:01.1
PCI: Sharing IRQ 11 with 0000:00:01.6
PCI: Sharing IRQ 11 with 0000:00:0a.0
Yenta: CardBus bridge found at 0000:00:03.0 [14ff:0601]
irq 10: nobody cared!
 [&lt;c0107c3e&gt;] __report_bad_irq+0x31/0x73
 [&lt;c0107ce4&gt;] note_interrupt+0x4c/0x6f
 [&lt;c0107ea2&gt;] do_IRQ+0x92/0xf9
 [&lt;c0106980&gt;] common_interrupt+0x18/0x20
 [&lt;c011c0dc&gt;] __do_softirq+0x2c/0x73
 [&lt;c011c145&gt;] do_softirq+0x22/0x26
 [&lt;c0107ef5&gt;] do_IRQ+0xe5/0xf9
 [&lt;c0106980&gt;] common_interrupt+0x18/0x20
 [&lt;c010e682&gt;] delay_tsc+0xd/0x15
 [&lt;c018e6c8&gt;] __delay+0xc/0xe
 [&lt;d6ad69f4&gt;] yenta_probe_irq+0xa9/0x102 [yenta_socket]
 [&lt;d6ad6ba3&gt;] yenta_get_socket_capabilities+0x2d/0x4e [yenta_socket]
 [&lt;d6ad6e4f&gt;] yenta_probe+0x19b/0x1e5 [yenta_socket]
 [&lt;c0193d31&gt;] pci_device_probe_static+0x2e/0x41
 [&lt;c0193d63&gt;] __pci_device_probe+0x1f/0x32
 [&lt;c0193d92&gt;] pci_device_probe+0x1c/0x31
 [&lt;c01d4537&gt;] bus_match+0x2e/0x4d
 [&lt;c01d460c&gt;] driver_attach+0x39/0x6e
 [&lt;c01d4970&gt;] bus_add_driver+0x58/0x70
 [&lt;c01d4cbf&gt;] driver_register+0x2d/0x31
 [&lt;c0193f36&gt;] pci_register_driver+0x4e/0x6b
 [&lt;d6a0000a&gt;] yenta_socket_init+0xa/0xc [yenta_socket]
 [&lt;c012b222&gt;] sys_init_module+0xe3/0x1d4
 [&lt;c0105f49&gt;] sysenter_past_esp+0x52/0x71
handlers:
[&lt;d6a9b20f&gt;] (usb_hcd_irq+0x0/0x4e [usbcore])
[&lt;d6a9b20f&gt;] (usb_hcd_irq+0x0/0x4e [usbcore])
Disabling IRQ #10
Yenta: ISA IRQ mask 0x0098, PCI irq 11
Socket status: 30000007
ohci1394: $Rev: 1223 $ Ben Collins &lt;bcollins@debian.org&gt;
PCI: Found IRQ 11 for device 0000:00:0a.0
PCI: Sharing IRQ 11 with 0000:00:01.1
PCI: Sharing IRQ 11 with 0000:00:01.6
PCI: Sharing IRQ 11 with 0000:00:03.0
ohci1394: fw-host0: Unexpected PCI resource length of 1000!
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[dff90000-dff907ff]  Max Packet=[2048]
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00012f6100038a1c]
NET: Registered protocol family 17
eth0: Media Link On 100mbps full-duplex
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02cc0c0(lo)
IPv6 over IPv4 tunneling driver


---

### Post by haha on 2004-10-23
I solved the problem...

i did 
==========
vi /etc/group   
==========

and search 

=========
audio:x:29
=========

and I changed that

=========
audio:x:29:$(my account)
=========

that's all

---

### Post by bluefreak on 2004-10-24
i cannot hear cd audio, but i can hear system sounds, such as when you click on a program link. furthermore, i can also hear the login tune.

my sound card is an ess allegro(integrated sound). i'm sure i have the correct modules loaded (maestro3)

i haven't tried playing mp3s, but cd audio cannot be heard when using any cd player or xmms...

i've tried tweaking the volume controls to no avail... and i've tried both oss and alsa sound drivers in xmms.

---

### Post by montgomj on 2004-10-24
Same problem here - no sound with cd player.  Sound with everything else (xmms, Rythmbox, oggs, mp3, Gnome system sounds).  Been running for about a week and this and samba remain my only difficult points.  I have ignored this one as I usually have my cds ripped to oggs and play them that way.

But would like to see a solution to the cd problem.

montgomj

---

### Post by LongTooth on 2004-10-24
I haven't gotten sound to work on my old PC. Something I'm going to get on. But the above problem reminds me of a solution on another machine. Namely the cable from the CD to the sound card. It was missing from the other machine I was working on and that solved the problem.

---

### Post by montgomj on 2004-10-24
Will check, as I did get an upgraded box from my employer just recently..........

Thanks

montgomj

---

### Post by bluefreak on 2004-10-25
well i tried playing an ogg file.... and guess what? it worked!

what's causing cd audio not to be heard?

cd audio works fine on windows on the other partition in the same computer.

---

### Post by mark on 2004-10-25
Oddly enough, I've been able to play audio CDs from the start. I've installed Ubuntu several times, trying different options, partitioning, etc., and it's just worked - no tweaking required. My hardware setup is pretty "vanilla" - an Intel D865GLC mainboard, using all on-board stuff (audio, LAN, video, etc.), no add-ons.
  
  Being fairly ignorant of audio stuff, I don't know what else to say.  If someone can reply, telling me what *conf* files (or whatever) are pertinent, I'd be glad to post mine here.
  
  Now, if I could just get RealPlayer to work....

---

### Post by bluefreak on 2004-11-02
i have no idea which files are related to this issue. i remember this no cd audio problem was present in damnsmalllinux too. but it has since been fixed(i think).

my ubuntu box is a pentium3 933mhz on an intel 82810 board. that's right... integrated audio and video. could the integrated audio(an ess maestro 3, allegro) be partially incompatible?

---

### Post by chibo on 2004-11-03
i have also some problems with sounds... actually quite big ones, because i can't get any sound out of my speakers. i have sound blaster live. any suggestions what conf files or something else i should check?

---

### Post by bluefreak on 2004-11-03
ok i fixed this no cd audio partially.

it seems that linux needs a cable form the cd drive to the sound card for analog cd audio output.

so i set xmms to use digital audio extraction via the configuration panel for the cd audio plugin.

i tried to play a cd by opening /dev/cdrom from xmms, but nothing happened. a hang occurs when loading .cda tracks from /cdrom (no /dev/) into the playlist, or opening the  /cdrom directory.

so i tried form the command line, by typing    xmms /cdrom    

it gave some error about missing libmikmod2.so ir something, but xmms launched and it works.

i used synaptic to install that missing lib, and now it works. however, dies anyone know how to play cds direct from xmms gui, instead of having to launch by console? 

oh forgot to mention... i have to use the root terminal to launch xmms which can play cds. typing the same command (xmms /cdrom) in the normal terminal gets no response.

---

### Post by bluefreak on 2004-11-03
i have made another discovery.

the instance of xmms that can play cds (the oe launched by typing command into the root terminal) can open load the cd tracks from /cdrom into the playlist, and can open the /cdrom directory and play it.

Even when i ran a audo xmms, the system hung while opening that directory. why is it the xmms launched from the root terminal is functioning properly and the one launched from the menu, or from typing 'xmms' into the application launcher, is not working properly.

however, both ways of launching xmms still can play ogg files on the hard drive.

---

### Post by Borgmeister on 2004-11-04
I havent tried any cd's, but i get sound problems in games ive got via apt-get. Chromium/Tuxracer/Frozen-bubble. Sound is gonna be fairly important for these. Unfortunately, i am using a laptop, so i cant connect an audio lead from the cd rom drive.

---

### Post by jwenting on 2004-11-04
[QUOTE=Borgmeister]I havent tried any cd's, but i get sound problems in games ive got via apt-get. Chromium/Tuxracer/Frozen-bubble. Sound is gonna be fairly important for these. Unfortunately, i am using a laptop, so i cant connect an audio lead from the cd rom drive.[/QUOTE]
 I don't know. I run it on a laptop and get CD sound just fine.
Apart from the login music I've not yet heard anything else though and the one mp3 I tried to play resulted in nothing but silence and a bunch of errors about unavailable support for the filetype.

---

### Post by Borgmeister on 2004-11-04
Hmm, battlestar glactica played back fine, so i am at a loss to where the problem lies, and, yes i have turned all the gmaes stuff up to full. Interesting huh?

---

### Post by jwenting on 2004-11-04
If audio CDs and DVD sound work, there's likely a problem with digital playback only.
CDs and DVDs are typically played through an analog channel, sometimes (depending on hardware) without any intervention from the CPU (and therefore the OS kernel) at all during playback (the only actions the OS would take are to start and stop playback and keep track of where on the disk we are).

---

### Post by bluefreak on 2004-12-10
[QUOTE=bluefreak]ok i fixed this no cd audio partially.

it seems that linux needs a cable form the cd drive to the sound card for analog cd audio output.

so i set xmms to use digital audio extraction via the configuration panel for the cd audio plugin.

i tried to play a cd by opening /dev/cdrom from xmms, but nothing happened. a hang occurs when loading .cda tracks from /cdrom (no /dev/) into the playlist, or opening the  /cdrom directory.

so i tried form the command line, by typing    xmms /cdrom    

it gave some error about missing libmikmod2.so ir something, but xmms launched and it works.

i used synaptic to install that missing lib, and now it works. however, dies anyone know how to play cds direct from xmms gui, instead of having to launch by console? 

oh forgot to mention... i have to use the root terminal to launch xmms which can play cds. typing the same command (xmms /cdrom) in the normal terminal gets no response.[/QUOTE]

after like more than i month i FINALLY know why xmms freezes. i use a proxy, and because cddb is enabled, it hangs because it cant send/recieve data from the cddb server. i just disable the cddb option, and now it works flawlessly. so now i need to figure out how to get xmms' cddb working through a proxy.

---

### Post by metlock on 2004-12-12
Howdy...Ubuntu Linux is great, but when I added a few sound/video programs (e.g. MPlayer, etc), I think I must have accidentally wiped out my volume control. I'm working on a Dell Latitude and sound works fine on WinXP.

On the little speaker in the top right corner of the screen, I can't raise the volume control. When right-clicking on the speaker and choosing Preferences, no Audio Channels appear.

Neither CDs or MP3s play in XMMS or MPlayer. Video (Quicktime or Windows Media) play without sound. It's as if my sound drivers are all gone.

Appreciate any help!

Metlock

---

### Post by berma on 2004-12-12
I have the same sound problems.
Plz, if somebody knows the solution post me as well.:-)
Thx!

---

### Post by berma on 2004-12-12
CD audio phisycally OK, but not in xmms
I installed cdtool and it works.
cdplay -d /dev/YOURDEV start
But what is wrong in xmms?

---

