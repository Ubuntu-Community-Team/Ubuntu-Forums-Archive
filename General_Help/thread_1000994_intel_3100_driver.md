---
title: "intel 3100 driver"
date: 2008-12-03
forum: General Help
---

### Post by t4ggs on 2008-12-03
Hi, I have a destop pc with an asus mobo and the video chip is from intel model 3100 is there any driver for it under intrepid?? in the case the answer is no...could compiz work??

if the answer is yet...how do i get it?

---

### Post by fragos on 2008-12-03
My Dell laptop uses that chip and the last 3 releases of Ubuntu installed with the X3100 working. On 8.10 Compiz is supported by X3100.

---

### Post by t4ggs on 2008-12-04
really? well when i go to system>admin>hardware drivers i cant see it.. how do i enable it?? because i tried in the appearence window in the Visual Effects tab enabling the effects i set them to normel and it gives me a message that the effects could not be ennabled.

---

### Post by Nathan Sweeney on 2008-12-04
> **t4ggs said:**
> really? well when i go to system>admin>hardware drivers i cant see it.. how do i enable it?? because i tried in the appearence window in the Visual Effects tab enabling the effects i set them to normel and it gives me a message that the effects could not be ennabled.

The System -> Administration -> Hardware Drivers tool only shows you any available proprietary drivers. Intel video is supported without proprietary drivers, so that is why it does not show up.

---

### Post by fragos on 2008-12-04
8.10 handles X configuration differently with automatic configuration. My laptop say no proprietary drivers used. I believe the Intel drivers must be open sourced. My laptop is running Compiz with the same options selected as my desktop which is Nvidia. when I run "sudo lspci" on the laptop it shows video as Intel GM965/GL960.

---

### Post by t4ggs on 2008-12-04
But i think mine is not enabled because compiz dont work...am i rigth?? how do i know if the diver is working???

---

### Post by fragos on 2008-12-04
Run "lsmod |grep intel_agp". I believe that is the driver name on my Dell.

---

### Post by t4ggs on 2008-12-04
lsmod |grep intel_agp returns nothing...what i did is: 

sudo lspci

gives me:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11) 
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) 
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25) 
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller 
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] 
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0) 
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) 
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) 
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller 
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91) 
00:09.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01) 
00:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) 
00:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) 
00:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51) 
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter



lsmod


gives me:

Module                  Size  Used by 
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge 
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep 
bluetooth              61924  6 rfcomm,bnep,sco,l2cap 
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats 
cpufreq_powersave       9856  0 
video                  25104  0 
output                 11008  1 video 
wmi                    14504  0 
pci_slot               12552  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter 
x_tables               22916  1 ip_tables 
ac                     12292  0 
lp                     17156  0 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0 
ac97_bus                9856  1 snd_ac97_codec 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss 
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss 
wlan_scan_sta          20608  1 
ath_rate_sample        19968  1 
snd_seq_dummy          10884  0 
evdev                  17696  6 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
pcspkr                 10624  0 
snd_rawmidi            29824  1 snd_seq_midi 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              29960  2 snd_pcm,snd_seq 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc 
soundcore              15328  1 snd 
button                 14224  0 
ath_pci                99096  0 
sis_agp                15232  1 
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm 
wlan                  211952  4 wlan_scan_sta,ath_rate_sample,ath_pci 
ath_hal               198864  3 ath_rate_sample,ath_pci 
agpgart                42184  1 sis_agp 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp 
i2c_sis96x             12420  0 
i2c_core               31892  1 i2c_sis96x 
ext3                  133384  1 
jbd                    55444  1 ext3 
mbcache                16004  1 ext3 
usbhid                 35840  0 
hid                    50560  1 usbhid 
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod 
sd_mod                 42264  6 
crc_t10dif              9984  1 sd_mod 
sg                     39732  0 
ehci_hcd               43276  0 
ohci_hcd               31888  0 
uhci_hcd               30736  0 
pata_sis               18436  4 
pata_acpi              12160  0 
ata_generic            12932  0 
sis900                 27904  0 
mii                    13440  1 sis900 
usbcore               148848  5 usbhid,ehci_hcd,ohci_hcd,uhci_hcd 
libata                177312  3 pata_sis,pata_acpi,ata_generic 
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata 
dock                   16656  1 libata 
thermal                23708  0 
processor              42156  1 thermal 
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon 
font                   16512  1 fbcon 
bitblit                13824  1 fbcon 
softcursor              9984  1 bitblit 
fuse                   60828  7 




and finally,  lsmod | grep intel

that gives me:

snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0 
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss 
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm

---

### Post by gabril on 2008-12-04
Dont complicate things...

$sudo aptitude install xserver-xorg-driver-intel
$sudo nano /etc/X11/xorg.conf

add under device "Driver   "intel""

---

### Post by t4ggs on 2008-12-04
> **gabril said:**
> Dont complicate things...

$sudo aptitude install xserver-xorg-driver-intel
$sudo nano /etc/X11/xorg.conf
did and after that..


add under device "Driver   "intel""
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "xserver-xorg-driver-intel"


do i need a repository??

---

### Post by fragos on 2008-12-04
You don't have an Intel video chip you have SIS. I'm not sure that SIS has the capabilities necessary for Compiz.

---

### Post by t4ggs on 2008-12-04
ops...i feel so stupid..well thank u anyway

---

### Post by fragos on 2008-12-04
> **t4ggs said:**
> ops...i feel so stupid..well thank u anyway

Learning is a process made one step at a time. Stupid are those that don't bother with the steps.

---

