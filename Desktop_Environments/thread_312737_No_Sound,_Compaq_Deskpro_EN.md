---
title: "No Sound, Compaq Deskpro EN"
date: 2006-12-04
forum: Desktop Environments
---

### Post by Erik123 on 2006-12-04
**RESOLVED**

This is a new install of Ubuntu 6.10 on a Compaq Deskpro EN SFF (866MHz).  The system seems to correctly report an "Intel 82801BA-ICH2" in Gnome Sound.    I've confirmed that the sound in not muted, and turned all the way up, but there is nothing.  Any suggestions would be greatly appreciated.  Following is some output that I hope will help:

[FONT="Courier New"]**home@desktop:~$ lspci**
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 01)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
home@desktop:~$ [/FONT]

[FONT="Courier New"]**home@desktop:~$ aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/FONT]

[FONT="Courier New"]**home@desktop:~$ lsmod**
Module                  Size  Used by
binfmt_misc            13448  1
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
speedstep_lib           5764  0
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  0
cpufreq_conservative     8712  0
video                  17540  0
tc1100_wmi              8324  0
sony_acpi               6412  0
sbs                    16804  0
pcc_acpi               14080  0
i2c_ec                  6272  1 sbs
hotkey                 11556  0
dev_acpi               12292  0
container               5632  0
button                  7952  0
battery                11652  0
asus_acpi              17688  0
ac                      6788  0
ipv6                  272288  8
af_packet              24584  2
lp                     12964  0
tsdev                   9152  0
snd_intel8x0           34844  1
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
i2c_i810                6276  0
i2c_algo_bit           10376  1 i2c_i810
i2c_core               23424  2 i2c_ec,i2c_algo_bit
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
floppy                 63044  0
evdev                  11392  1
e100                   38020  0
mii                     6912  1 e100
psmouse                41352  0
pcspkr                  4352  0
intel_agp              26012  1
agpgart                34888  2 intel_agp
serio_raw               8452  0
hw_random               7320  0
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
parport_pc             37796  1
parport                39496  2 lp,parport_pc
ext3                  142728  1
jbd                    62228  1 ext3
uhci_hcd               24968  0
usbcore               134912  2 uhci_hcd
ide_generic             2432  0
ide_cd                 33696  0
cdrom                  38944  1 ide_cd
ide_disk               18560  3
piix                   11780  1
generic                 5764  0
thermal                15624  0
processor              31560  1 thermal
fan                     6020  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability[/FONT]

---

