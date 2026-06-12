---
title: "Nautilus is crashing my system"
date: 2005-05-08
forum: Desktop Environments
---

### Post by dcviana on 2005-05-08
Hi there folks

I have been using hoary for a dew days, and I kinda liked it. Unfortunately the world is not perfect and I´ve encountered an error while using it.

Sometimes when I try to open a file or view its properties in Nautilus, it causes my system to have high HD activity, so high that the system is unusable after that. Even te mouse moves in slow motion cause of that. This problem happens at random times (most of the time nautilus runs perfectly).

I noticed that it only happens with nautilus, but haven´t found any other pattern that cause the error. It happened with different files of different types and in different partitions.

Here is my sistem:
Athlon XP 2200+
512MB RAM
20GB HD
ATI Radeon 9600 PRO video card, using ATI driver instaled from the restricted tree.
Shuttle MN31N (NFORCE 2) MBoard

---

### Post by bigbangbigbigbang on 2005-05-08
Hi

Could you send the output of  (run as root or with sudo): hdparm /dev/hda,
lspci and lsmod.

---

### Post by LongTooth on 2005-05-08
How do you activate Nautilus? It just might help in shooting trouble.

---

### Post by dcviana on 2005-05-08
Hi guys

Something that might help, everytime it happens I'm using firefox (Original from ubuntu cd) and aMSN (instaled from universal apt sources).

Here is some info of my system

=========================================
HDPARM Output

sudo hdparm /dev/hda
Password:

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 39549/16/63, sectors = 20411080704, start = 0

=========================================
LSPCI Output

sudo lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
0000:01:06.0 Communication controller: Lucent Microelectronics 56k WinModem (rev 01)
0000:03:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
0000:03:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

=========================================
LSMOD Output
sudo lsmod
Module                  Size  Used by
isofs                  33720  1
udf                    77060  0
fglrx                 229568  7
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  6
ohci1394               31876  0
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
af_packet              20744  2
snd_intel8x0           29984  1
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
usbhid                 29376  0
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
forcedeth              16128  0
ehci_hcd               29444  0
ohci_hcd               19848  0
usbcore               107384  4 usbhid,ehci_hcd,ohci_hcd
i2c_nforce2             6400  0
i2c_core               21264  1 i2c_nforce2
nvidia_agp              7452  1
agpgart                31784  2 nvidia_agp
analog                 10784  0
gameport                4608  1 analog
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
nls_cp437               5888  2
ntfs                   97136  1
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
evdev                   9088  0
tsdev                   7488  0
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              119936  2 sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  1
cdrom                  36508  2 sr_mod,ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
ide_disk               18176  4
amd74xx                13340  1
ide_core              118988  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   26164  568
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
=========================================


I running nautilus via Applications=>System tools=>File navigator (don know if the english name is File navigator, my system is in portuguese).

Thanks for your attention.

---

### Post by bigbangbigbigbang on 2005-05-08
Hi 

your nvidia chipset is known to have caused stability problems with several linux kernels.
try to add "noapic nolapic" bootparams to the kernel the following way:

edit /boot/grub/menu.lst and change your kernel line to the following

kernel       /vmlinuz-2.6.10-5-686 root=(your rootdevice) ro noapic nolapic quiet splash


let us know if it helps

---

### Post by dcviana on 2005-05-09
Hi guys

I tried the noapic and nolapic thing but it didn't work. I think I have pinpointed the problem. It appears to happen when Nautilus try to preview a file it doesn't suport, or is corrupted. I have a folder with my videos and some are wmv or realplayer. Some of them lock Totem when I try to open it (i simply close without giving any message) and when I open the folder in Nautilus is when the problem seems to happen.

I tried disabling preview and I think it fixed the problem (it didn't caused the high load of HD anymore). Anyway if it's confirmed, it should be considered a bug in nautilus, cause in my previous Conectiva 10 instalation when nautilus couldn't preview a file, it simply didn't preview it, but didn't lock my system.

Anyway, thanks for the help.

---

