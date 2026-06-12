---
title: "no sound!"
date: 2005-08-31
forum: Desktop Environments
---

### Post by vkkim on 2005-08-31
Hi, I posted this in another forum but I'm not getting much help so I thought I might come here for help...

[http://ubuntuforums.org/showthread.php?t=47048](http://ubuntuforums.org/showthread.php?t=47048)

---

### Post by JOKe on 2005-08-31
[QUOTE=vkkim]Hi, I posted this in another forum but I'm not getting much help so I thought I might come here for help...

[http://ubuntuforums.org/showthread.php?t=47048](http://ubuntuforums.org/showthread.php?t=47048)[/QUOTE]
i think there is little problem in ubuntus gnome becouse it starts sound system by default so the oss and alsa inputs are bussy by this Gnome Sound System so:

#1st
if you  dont have any sound
please give us
lspci
lsmod
give the output to help you

#2th
if you have sound in gnome but dont have another sound :
i think there is little problem in ubuntus gnome becouse it starts sound system by default so the oss and alsa inputs are bussy by this Gnome Sound System so go to Sound Preference and uncehck the box called Start Sound System on startup or somethink like this. :)
ALT+CTRL+BACKSPACE and maybe you will have sound :)

---

### Post by vkkim on 2005-08-31
lspci:

0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 855GME GMCH Host-to-AGP Bridge (Virtual PCI-to-PCI) (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 Network controller: Intel Corp.: Unknown device 4223 (rev 05)
0000:02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 88)
0000:02:05.1 System peripheral: Ricoh Co Ltd: Unknown device 0575


lsmod:

Module                  Size  Used by
nls_utf8                2176  0
nls_cp437               5888  0
vfat                   12928  0
fat                    37792  1 vfat
sd_mod                 16784  0
usb_storage            64064  0
scsi_mod              119936  2 sd_mod,usb_storage
button                  6800  0
ehci_hcd               29444  0
uhci_hcd               30224  0
ipw2200                66156  0
8139too                24320  0
speedstep_centrino      7892  1
proc_intf               4100  0
freq_table              4100  1 speedstep_centrino
cpufreq_userspace       4572  1
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  2
video                  16260  0
sony_acpi               6280  0
i915                   18304  1
drm                    59412  2 i915
battery                10244  0
container               4608  0
ac                      4996  3
ipv6                  229504  9
af_packet              20744  2
yenta_socket           19584  0
arc4                    2048  1
ieee80211_crypt_wep     4932  1
pcmcia_core            53568  2 pcmcia,yenta_socket
firmware_class          9728  1 ipw2200
ieee80211              21252  1 ipw2200
ieee80211_crypt         5832  2 ieee80211_crypt_wep,ieee80211
8139cp                 19200  0
mii                     4736  2 8139too,8139cp
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
hw_random               5524  0
usbcore               107384  4 usb_storage,ehci_hcd,uhci_hcd
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
intel_agp              20636  1
agpgart                31784  3 drm,intel_agp
rtc                    12216  0
pcspkr                  3816  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
pcc_acpi               11264  0
evdev                   9088  1
joydev                  9408  0
tsdev                   7488  0
snd_intel8x0           30144  1
snd_ac97_codec         66040  1 snd_intel8x0
snd_pcm_oss            47648  0
snd_pcm                82184  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
snd_mixer_oss          16768  2 snd_pcm_oss
snd                    51300  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9824  2 snd
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  0
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix                   26164  974
thermal                13576  0
processor              22708  2 speedstep_centrino,thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

Already tried #2...

---

