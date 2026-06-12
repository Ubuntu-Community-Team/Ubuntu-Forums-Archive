---
title: "CDROM missing"
date: 2006-08-22
forum: Desktop Environments
---

### Post by canter690 on 2006-08-22
Hi

Installed my Ubuntu 6.06 last week. Everything seemed ok, expect that now I noticed that I cant see my DVD or CDROM (CDRW).

Various files and output for your review to see if there is something glaringly wrong.

Device Manager seems to show all my devices except for the IDE devices.

I have a SATA drive which is mapped via the BIOS as the Primary master IDE channel 0.

My DVD and CDROM are configured as the master and slave on IDE Channel 1.

They appear during the BIOS boot up.  Cant see them under linux.  

   

lspci

0000:00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
0000:00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9700 Pro] (Secondary)
0000:02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller (LOM)
0000:03:04.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:03:04.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:03:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
0000:03:0c.0 RAID bus controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (PCI version seems to be IT8212, embedded seems (rev 10)

Cant seem to see any IDE devices

The CDROM and DVD definatley work as I am able to boot the Ubuntu CD.

No entries in /dev for

/dev/scd0
/dev/cdrom

fdisk -l shows disk
Disk /dev/sda: 120.0 GB, 120033041920 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14215   114181956   83  Linux
/dev/sda2           14216       14593     3036285    5  Extended
/dev/sda5           14216       14593     3036253+  82  Linux swap / Solaris

Disk /dev/hda: 240.0 GB, 240068231168 bytes
255 heads, 63 sectors/track, 29186 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       29186   234436513+  83  Linux

Have noticed that Disks Manager has /dev/scd0 listed as a hard disk with no  other useful info on the device

No entry that might be the DVD in Disks Manager

Any guidance greatly appreciated.

---

### Post by taurus on 2006-08-22
You mean after you insert a CD/DVD into the drive, it doesn't mount and you can't mount it by hand!

What does your /etc/fstab look like then?

```
more /etc/fstab
```

---

### Post by canter690 on 2006-08-22
Hi

At boot up or even when I insert a disc into either drive - cant see the devices.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by canter690 on 2006-08-22
hi

Was just doing some more investigation and noticed that lsmod did not contain a module called cdrom (which appeared in someone elses output from lsmod elsewhere).  Should this module be loaded or is it simply a symptom of not seeing the IDE interface or CDROM in the first instance.  If it should be loaded how do I load it.

FYI lsmod output below
Module                  Size  Used by
isofs                  37688  0 
udf                    88452  0 
rfcomm                 40216  0 
l2cap                  26244  5 rfcomm
ppdev                   9220  0 
fglrx                 388908  44 
speedstep_lib           4484  0 
cpufreq_userspace       4696  0 
cpufreq_stats           5636  0 
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        6428  0 
cpufreq_conservative     7332  0 
video                  16260  0 
tc1100_wmi              6916  0 
sony_acpi               5644  0 
pcc_acpi               12416  0 
hotkey                 11556  0 
dev_acpi               11140  0 
container               4608  0 
button                  6672  0 
acpi_sbs               19980  0 
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 58936  1 
md_mod                 72532  0 
ipv6                  265728  10 
sbp2                   24196  0 
lp                     11844  0 
af_packet              22920  2 
ide_disk               17664  1 
parport_pc             35780  1 
parport                36296  3 ppdev,lp,parport_pc
analog                 12320  0 
floppy                 62148  0 
tsdev                   8000  0 
gameport               15496  1 analog
snd_usb_audio          79296  0 
snd_usb_lib            16640  1 snd_usb_audio
snd_rawmidi            25504  1 snd_usb_lib
snd_seq_device          8716  1 snd_rawmidi
pcspkr                  2180  0 
rtc                    13492  0 
bt878                  10552  0 
tuner                  42276  0 
spca5xx               630928  0 
usbhid                 39904  0 
snd_hwdep               9376  1 snd_usb_audio
psmouse                36100  0 
hci_usb                16660  2 
serio_raw               7300  0 
snd_intel8x0           33692  1 
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
bluetooth              49892  7 rfcomm,l2cap,hci_usb
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
it821x                  8708  0 [permanent]
snd_pcm                89864  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
bttv                  164304  1 bt878
video_buf              22148  1 bttv
i2c_algo_bit            9608  1 bttv
snd_timer              25220  1 snd_pcm
snd                    55268  12 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
v4l2_common             6016  1 bttv
btcx_risc               5128  1 bttv
tveeprom               15248  1 bttv
i2c_core               21904  5 i2c_acpi_ec,tuner,bttv,i2c_algo_bit,tveeprom
e1000                 118840  0 
videodev                9856  2 spca5xx,bttv
intel_agp              22940  1 
agpgart                34888  2 fglrx,intel_agp
shpchp                 45632  0 
pci_hotplug            29236  1 shpchp
sg                     37920  0 
evdev                   9856  1 
ext3                  135688  1 
jbd                    58772  1 ext3
ide_generic             1536  0 
ohci1394               35124  0 
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0 
uhci_hcd               33680  0 
usbcore               130692  8 snd_usb_audio,snd_usb_lib,spca5xx,usbhid,hci_usb,ehci_hcd,uhci_hcd
sd_mod                 19984  3 
generic                 5124  0 
ata_piix               11012  4 
libata                 78992  1 ata_piix
scsi_mod              139496  4 sbp2,sg,sd_mod,libata
thermal                13576  0 
processor              23360  1 thermal
fan                     4868  0 
capability              5000  0 
commoncap               7296  1 capability
vga16fb                13704  1 
vgastate               10368  1 vga16fb
fbcon                  42784  72 
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
sam@big-beast:~$ lsmod | ata
bash: ata: command not found
sam@big-beast:~$ lsmod | grep ata
ata_piix               11012  4 
libata                 78992  1 ata_piix
scsi_mod              139496  4 sbp2,sg,sd_mod,libata
sam@big-beast:~$ lsmod | grep cdrom
sam@big-beast:~$ lsmod
Module                  Size  Used by
isofs                  37688  0 
udf                    88452  0 
rfcomm                 40216  0 
l2cap                  26244  5 rfcomm
ppdev                   9220  0 
fglrx                 388908  48 
speedstep_lib           4484  0 
cpufreq_userspace       4696  0 
cpufreq_stats           5636  0 
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        6428  0 
cpufreq_conservative     7332  0 
video                  16260  0 
tc1100_wmi              6916  0 
sony_acpi               5644  0 
pcc_acpi               12416  0 
hotkey                 11556  0 
dev_acpi               11140  0 
container               4608  0 
button                  6672  0 
acpi_sbs               19980  0 
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 58936  1 
md_mod                 72532  0 
ipv6                  265728  10 
sbp2                   24196  0 
lp                     11844  0 
af_packet              22920  2 
ide_disk               17664  1 
parport_pc             35780  1 
parport                36296  3 ppdev,lp,parport_pc
analog                 12320  0 
floppy                 62148  0 
tsdev                   8000  0 
gameport               15496  1 analog
snd_usb_audio          79296  1 
snd_usb_lib            16640  1 snd_usb_audio
snd_rawmidi            25504  1 snd_usb_lib
snd_seq_device          8716  1 snd_rawmidi
pcspkr                  2180  0 
rtc                    13492  0 
bt878                  10552  0 
tuner                  42276  0 
spca5xx               630928  0 
usbhid                 39904  0 
snd_hwdep               9376  1 snd_usb_audio
psmouse                36100  0 
hci_usb                16660  2 
serio_raw               7300  0 
snd_intel8x0           33692  2 
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
bluetooth              49892  7 rfcomm,l2cap,hci_usb
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  3 snd_pcm_oss
it821x                  8708  0 [permanent]
snd_pcm                89864  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
bttv                  164304  1 bt878
video_buf              22148  1 bttv
i2c_algo_bit            9608  1 bttv
snd_timer              25220  1 snd_pcm
snd                    55268  12 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  3 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
v4l2_common             6016  1 bttv
btcx_risc               5128  1 bttv
tveeprom               15248  1 bttv
i2c_core               21904  5 i2c_acpi_ec,tuner,bttv,i2c_algo_bit,tveeprom
e1000                 118840  0 
videodev                9856  2 spca5xx,bttv
intel_agp              22940  1 
agpgart                34888  2 fglrx,intel_agp
shpchp                 45632  0 
pci_hotplug            29236  1 shpchp
sg                     37920  0 
evdev                   9856  1 
ext3                  135688  1 
jbd                    58772  1 ext3
ide_generic             1536  0 
ohci1394               35124  0 
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0 
uhci_hcd               33680  0 
usbcore               130692  8 snd_usb_audio,snd_usb_lib,spca5xx,usbhid,hci_usb,ehci_hcd,uhci_hcd
sd_mod                 19984  3 
generic                 5124  0 
ata_piix               11012  4 
libata                 78992  1 ata_piix
scsi_mod              139496  4 sbp2,sg,sd_mod,libata
thermal                13576  0 
processor              23360  1 thermal
fan                     4868  0 
capability              5000  0 
commoncap               7296  1 capability
vga16fb                13704  1 
vgastate               10368  1 vga16fb
fbcon                  42784  72 
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit


Thanks

---

### Post by canter690 on 2006-08-22
OK as I continue to debug I will post what I have learnt in case this helps.

Just booted from the CD ( am installing a fresh copy on a new partition ).  Opened Device Manager and noticed that the CDROM and DVD are under the ICH5 SATA controller as SCSI devices.  

I susspect this is a quirk with my BIOS setup.  I have mapped the SATA as an IDE drive under the BIOS options.  If this is casusing the problem then I hope someone can provide advice on how to work around this. I would see this as a bug.

Advice ?

---

### Post by canter690 on 2006-08-22
well....

this feels like I am talking with myself here but hpope this helps others in what I have learnt.

SO just remapped the SATA as SATA drive and not IDE under the BIOS.  

Noticed that my mounting of the root filesystem was much faster....and my CDROM and DVD now appeared.  

So as I said before I would see this as bug but at least I have my CDROM working now.
:)

---

