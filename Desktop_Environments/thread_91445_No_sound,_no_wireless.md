---
title: "No sound, no wireless"
date: 2005-11-17
forum: Desktop Environments
---

### Post by Ethan_bennett on 2005-11-17
Ok, Here's my dilemma. I just painlessly installed Unbuntu. Now, for some reason, my sound and my wireless don't work. I have already tried the ndiswrapper. I used ndisgtk to install, failed. Then I went the terminal approach, here's what I got in dmesg:

(boot messages)
[4297860.773000] ndiswrapper version 1.1 loaded (preempt=no,smp=yes)
[4297860.780000] ndiswrapper: driver netwg121 (NETGEAR, Inc.,11/13/2003, 1.0.5.1000) loaded
[4297866.434000] ndiswrapper (NdisWriteErrorLogEntry:273): log: C000138A, count: 3 (c0000001), return address: fa28ac5f, entry: fa29d2a3 offset: 4294891964
[4297866.881000] ndiswrapper (ndiswrapper_add_one_usb_dev:312): Windows driver couldn't initialize the device (C0010006)
[4297866.881000] ndiswrapper: probe of 3-3:1.0 failed with error -22
[4297866.881000] usbcore: registered new driver ndiswrapper

My sound appears to work fine, as the driver for my onboard Cmedia controller is installed, but I get no sound. I've gone into the alsamixer, and made sure everything was on. I went into the Multimedia System Selector, and changed from OSS to ALSA to ESD. None work, and when I click "test," it says that it can't make a test pipeline. Here's my lsmod and lspci:

000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f1 (rev a2)
0000:02:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

Module                  Size  Used by
ndiswrapper           133132  0
nls_cp437               6208  1
isofs                  37564  1
udf                    93444  0
rfcomm                 41304  0
l2cap                  28672  5 rfcomm
bluetooth              52100  4 rfcomm,l2cap
powernow_k8            14112  0
cpufreq_userspace       6496  1
cpufreq_stats           6400  0
freq_table              5024  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2240  0
cpufreq_ondemand        7528  0
cpufreq_conservative     8460  0
video                  16324  0
tc1100_wmi              7236  0
sony_acpi               5836  0
pcc_acpi               11648  0
hotkey                  9828  0
dev_acpi               11780  0
i2c_acpi_ec             6016  0
button                  6992  0
battery                 9860  0
container               4928  0
ac                      5252  0
ipv6                  266144  6
af_packet              24456  2
pcspkr                  4168  0
rtc                    13960  0
snd_cmipci             35680  6
gameport               16520  1 snd_cmipci
snd_pcm_oss            54432  0
snd_mixer_oss          19904  1 snd_pcm_oss
snd_pcm                93316  3 snd_cmipci,snd_pcm_oss
snd_page_alloc         11144  1 snd_pcm
snd_opl3_lib           11584  1 snd_cmipci
snd_timer              26244  4 snd_pcm,snd_opl3_lib
snd_hwdep               9568  1 snd_opl3_lib
snd_mpu401_uart         8512  1 snd_cmipci
snd_rawmidi            26528  1 snd_mpu401_uart
snd_seq_device          9036  2 snd_opl3_lib,snd_rawmidi
snd                    58212  19 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10464  1 snd
ohci1394               35892  0
shpchp                 98308  0
pci_hotplug            28796  1 shpchp
i2c_nforce2             7296  0
i2c_core               22080  2 i2c_acpi_ec,i2c_nforce2
amd64_agp              12808  1
dm_mod                 59808  1
tsdev                   8320  0
evdev                  10240  0
nvidia               3713476  12
agpgart                35724  2 amd64_agp,nvidia
sr_mod                 17892  0
sbp2                   24072  0
ieee1394              104312  2 ohci1394,sbp2
psmouse                30916  0
mousedev               12452  1
parport_pc             36740  1
lp                     12900  0
parport                37768  2 parport_pc,lp
md                     47824  0
ext3                  139976  1
jbd                    60312  1 ext3
mbcache                10436  1 ext3
thermal                13640  0Module                  Size  Used by
ndiswrapper           133132  0
nls_cp437               6208  1
isofs                  37564  1
udf                    93444  0
rfcomm                 41304  0
l2cap                  28672  5 rfcomm
bluetooth              52100  4 rfcomm,l2cap
powernow_k8            14112  0
cpufreq_userspace       6496  1
cpufreq_stats           6400  0
freq_table              5024  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2240  0
cpufreq_ondemand        7528  0
cpufreq_conservative     8460  0
video                  16324  0
tc1100_wmi              7236  0
sony_acpi               5836  0
pcc_acpi               11648  0
hotkey                  9828  0
dev_acpi               11780  0
i2c_acpi_ec             6016  0
button                  6992  0
battery                 9860  0
container               4928  0
ac                      5252  0
ipv6                  266144  6
af_packet              24456  2
pcspkr                  4168  0
rtc                    13960  0
snd_cmipci             35680  6
gameport               16520  1 snd_cmipci
snd_pcm_oss            54432  0
snd_mixer_oss          19904  1 snd_pcm_oss
snd_pcm                93316  3 snd_cmipci,snd_pcm_oss
snd_page_alloc         11144  1 snd_pcm
snd_opl3_lib           11584  1 snd_cmipci
snd_timer              26244  4 snd_pcm,snd_opl3_lib
snd_hwdep               9568  1 snd_opl3_lib
snd_mpu401_uart         8512  1 snd_cmipci
snd_rawmidi            26528  1 snd_mpu401_uart
snd_seq_device          9036  2 snd_opl3_lib,snd_rawmidi
snd                    58212  19 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10464  1 snd
ohci1394               35892  0
shpchp                 98308  0
pci_hotplug            28796  1 shpchp
i2c_nforce2             7296  0
i2c_core               22080  2 i2c_acpi_ec,i2c_nforce2
amd64_agp              12808  1
dm_mod                 59808  1
tsdev                   8320  0
evdev                  10240  0
nvidia               3713476  12
agpgart                35724  2 amd64_agp,nvidia
sr_mod                 17892  0
sbp2                   24072  0
ieee1394              104312  2 ohci1394,sbp2
psmouse                30916  0
mousedev               12452  1
parport_pc             36740  1
lp                     12900  0
parport                37768  2 parport_pc,lp
md                     47824  0
ext3                  139976  1
jbd                    60312  1 ext3
mbcache                10436  1 ext3
thermal                13640  0
processor              24104  2 powernow_k8,thermal
fan                     4996  0
forcedeth              23424  0
ehci_hcd               36104  0
ohci_hcd               22276  0
usbcore               121724  4 ndiswrapper,ehci_hcd,ohci_hcd
ide_cd                 42564  1
cdrom                  40544  2 sr_mod,ide_cd
ide_disk               19200  3
ide_generic             1920  0
sata_nv                10116  0
libata                 54980  1 sata_nv
scsi_mod              138376  3 sr_mod,sbp2,libata
amd74xx                14492  1
ide_core              141108  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   30160  558
vesafb                  8536  0
capability              5256  0
commoncap               7360  1 capability
vga16fb                13160  1
vgastate               10240  1 vga16fb
softcursor              2944  2 vesafb,vga16fb
cfbimgblt               3456  2 vesafb,vga16fb
cfbfillrect             4416  2 vesafb,vga16fb
cfbcopyarea             5120  2 vesafb,vga16fb
fbcon                  39744  72
tileblit                2880  1 fbcon
font                    8768  1 fbcon
bitblit                 6144  1 fbcon

processor              24104  2 powernow_k8,thermal
fan                     4996  0
forcedeth              23424  0
ehci_hcd               36104  0
ohci_hcd               22276  0
usbcore               121724  4 ndiswrapper,ehci_hcd,ohci_hcd
ide_cd                 42564  1
cdrom                  40544  2 sr_mod,ide_cd
ide_disk               19200  3
ide_generic             1920  0
sata_nv                10116  0
libata                 54980  1 sata_nv
scsi_mod              138376  3 sr_mod,sbp2,libata
amd74xx                14492  1
ide_core              141108  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   30160  558
vesafb                  8536  0
capability              5256  0
commoncap               7360  1 capability
vga16fb                13160  1
vgastate               10240  1 vga16fb
softcursor              2944  2 vesafb,vga16fb
cfbimgblt               3456  2 vesafb,vga16fb
cfbfillrect             4416  2 vesafb,vga16fb
cfbcopyarea             5120  2 vesafb,vga16fb
fbcon                  39744  72
tileblit                2880  1 fbcon
font                    8768  1 fbcon
bitblit                 6144  1 fbcon

---

