---
title: "everything is oversized in ubuntu"
date: 2008-07-27
forum: Desktop Environments
---

### Post by bolter40k on 2008-07-27
i just recently reinstalled ubuntu after previous problems and now its working almost perfectly, however everything is oversized.  Icons, text, windows, toolbars, and even the menus.

I tried adjusting the resolution but its stuck on 640x480. 
I tried changing the themes and that didnt work.
I think its because i have absolutely no drivers installed and ubuntu cant seem to detect my hardware.
Previously i had 8.04 installed and i never had the=is problem before, maybe it has something to do with the fact that i installed from the graphics safe settings on the boot disk...

---

### Post by loboc on 2008-07-27
What kind of graphics card do you have and what drivers are loaded; 

Copy paste the results of ```
lspci
``` and ```
lsmod
``` to the forum

---

### Post by loboc on 2008-07-27
```
displayconfig-gtk&
```

Should let you select the driver and display settings.  Problem is you may not have the drivers for you card installed from the cd.  Newer ATI and NVIDIA cards perform better using proprietary drivers not included on the CD due to licensing

---

### Post by bolter40k on 2008-07-27
> **loboc said:**
> What kind of graphics card do you have and what drivers are loaded; 

Copy paste the results of ```
lspci
``` and ```
lsmod
``` to the forum

lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

lsmod

Module                  Size  Used by
ipv6                  267780  8 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
evdev                  13056  2 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
psmouse                40336  0 
serio_raw               7940  0 
pcspkr                  4224  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
button                  9232  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
shpchp                 34452  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
pci_hotplug            30880  1 shpchp
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
i2c_i810                5636  0 
intel_agp              25492  1 
i2c_algo_bit            7300  1 i2c_i810
agpgart                34760  1 intel_agp
i2c_core               24832  2 i2c_i810,i2c_algo_bit
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
pata_acpi               8320  0 
floppy                 59588  0 
ata_piix               19588  2 
e100                   37388  0 
mii                     6400  1 e100
libata                159344  3 ata_generic,pata_acpi,ata_piix
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 


ill try the second in a second thx for your help

---

### Post by bolter40k on 2008-07-27
> **loboc said:**
> ```
displayconfig-gtk&
```

Should let you select the driver and display settings.  Problem is you may not have the drivers for you card installed from the cd.  Newer ATI and NVIDIA cards perform better using proprietary drivers not included on the CD due to licensing

everything is greyed out and it says that i need admin properties but i am the only account

---

### Post by loboc on 2008-07-27
you need to use sudo to elevate the rights of that command 

also apparently your bios settings need to be adjusted

[http://ubuntuforums.org/archive/index.php/t-256470.html](http://ubuntuforums.org/archive/index.php/t-256470.html)

There is also a package called 915resolution but I am not familar with it 

```
 sudo apt-get install 915resolution 
```

---

### Post by loboc on 2008-07-27
sorry i forgot sudo I am going to get some food good luck for now

---

### Post by bolter40k on 2008-07-27
> **loboc said:**
> you need to use sudo to elevate the rights of that command 

also apparently your bios settings need to be adjusted

[http://ubuntuforums.org/archive/index.php/t-256470.html](http://ubuntuforums.org/archive/index.php/t-256470.html)

There is also a package called 915resolution but I am not familar with it 

```
 sudo apt-get install 915resolution 
```

the bios worked i changed it from 1mb to 8mb Thank You

---

