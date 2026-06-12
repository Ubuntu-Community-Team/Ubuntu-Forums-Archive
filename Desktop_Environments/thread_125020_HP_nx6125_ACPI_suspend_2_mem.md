---
title: "HP nx6125 ACPI suspend 2 mem"
date: 2006-02-02
forum: Desktop Environments
---

### Post by Mansor on 2006-02-02
Hi everyone, I've just buy a HP Compaq nx6125 Sempron 2800.
Everything it's ok, I've followed some installation issues but I can't use suspend to memory.

This is my info
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:04.0 PCI bridge: ATI Technologies Inc: Unknown device 5a36
0000:00:05.0 PCI bridge: ATI Technologies Inc: Unknown device 5a37
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5955
0000:02:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
0000:02:02.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
0000:02:04.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:02:04.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:02:04.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:02:04.4 0805: Texas Instruments: Unknown device 8034

lsmod

Module                  Size  Used by
usbhid                 35552  0
isofs                  36664  1
loop                   17480  2
ipv6                  252544  6
rfcomm                 38748  0
l2cap                  25156  5 rfcomm
bluetooth              48580  4 rfcomm,l2cap
powernow_k8            12424  0
cpufreq_userspace       4380  1
cpufreq_stats           5316  0
freq_table              4484  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1792  0
cpufreq_ondemand        6108  0
cpufreq_conservative     7012  0
pcmcia                 26632  2
fglrx                 255780  7
video                  15812  0
tc1100_wmi              6788  0
sony_acpi               5388  0
pcc_acpi               11200  0
hotkey                  9380  0
dev_acpi               11268  0
i2c_acpi_ec             5568  0
i2c_core               21328  1 i2c_acpi_ec
button                  6544  0
battery                 9412  0
container               4480  0
ac                      4804  0
af_packet              22088  4
rtc                    12408  0
pcspkr                  3460  0
ohci1394               34804  0
yenta_socket           25356  1
rsrc_nonstatic         13504  1 yenta_socket
pcmcia_core            49668  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_atiixp             20384  1
snd_ac97_codec         84028  1 snd_atiixp
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  1 snd_pcm
snd                    55172  8 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  1 snd
snd_page_alloc         10696  2 snd_atiixp,snd_pcm
pci_hotplug            27636  0
ati_agp                 9100  0
agpgart                34888  2 fglrx,ati_agp
nls_cp437               5760  1
ntfs                  109104  1
dm_mod                 58044  1
joydev                 10048  0
tsdev                   7872  0
evdev                   9728  1
ndiswrapper           132296  0
sr_mod                 17252  0
sbp2                   23176  0
scsi_mod              135944  2 sr_mod,sbp2
ieee1394              101752  2 ohci1394,sbp2
psmouse                30212  0
mousedev               11680  1
parport_pc             35460  1
lp                     12420  0
parport                36104  2 parport_pc,lp
md                     45648  0
ext3                  137352  2
jbd                    55128  1 ext3
mbcache                 9348  1 ext3
thermal                13064  0
processor              22908  2 powernow_k8,thermal
fan                     4548  0
tg3                    97220  0
ehci_hcd               34312  0
ohci_hcd               20740  0
usbcore               118396  5 usbhid,ndiswrapper,ehci_hcd,ohci_hcd
ide_cd                 41732  0
cdrom                  39904  2 sr_mod,ide_cd
ide_disk               18560  5
ide_generic             1472  0
atiixp                  6096  1
ide_core              139028  4 ide_cd,ide_disk,ide_generic,atiixp
unix                   27248  756
capability              4808  0
commoncap               6912  1 capability
vesafb                  8088  1
vgastate                9792  0
softcursor              2496  1 vesafb
cfbimgblt               3008  1 vesafb
cfbfillrect             3968  1 vesafb
cfbcopyarea             4672  1 vesafb
fbcon                  39104  72
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 5696  1 fbcon

Thanks to all linux community

---

