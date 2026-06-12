---
title: "Hal won't start"
date: 2006-02-06
forum: Desktop Environments
---

### Post by eyelessfade on 2006-02-06
When I try to start hal on my new installed kubuntu 5.10 Breezy I get the following error:

```

sudo /etc/init.d/dbus restart
 * Stopping Hardware abstraction layer:
/etc/dbus-1/event.d/20hal: line 49: kill: (20278) - No such process
   ...done.
 * Stopping system message bus...
   ...done.
 * Starting system message bus...
   ...done.
 * Starting Hardware abstraction layer:
run-parts: /etc/dbus-1/event.d/20hal exited with return code 2

```
lspci gives the following, which I don't like:
```

0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00ea (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a4)
0000:02:0a.0 FireWire (IEEE 1394): Texas Instruments PCILynx/PCILynx2 IEEE 1394 Link Layer Controller (rev 02)

```
But it seems that all the modules loads right:

```

Module                  Size  Used by
nfsd                  218560  9
exportfs                5760  1 nfsd
lockd                  63784  2 nfsd
sunrpc                137796  12 nfsd,lockd
ehci_hcd               34248  0
ohci_hcd               20644  0
isofs                  35960  1
udf                    90820  0
nls_iso8859_1           4000  0
nls_cp437               5664  0
vfat                   13440  0
fat                    52668  1 vfat
nvidia               3922620  0
rfcomm                 38460  0
l2cap                  24740  5 rfcomm
bluetooth              48356  2 rfcomm,l2cap
cpufreq_powersave       1696  0
cpufreq_stats           5252  0
cpufreq_userspace       4316  0
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
freq_table              4388  1 cpufreq_stats
capifs                  5768  1
tc1100_wmi              6692  0
video                  15748  0
battery                 9348  0
container               4384  0
i2c_acpi_ec             5472  0
button                  6480  0
pcc_acpi               11104  0
sony_acpi               5324  0
ac                      4708  0
dev_acpi               11108  0
hotkey                  9284  0
ipv6                  251232  12
sd_mod                 19120  0
af_packet              21768  2
tsdev                   7776  0
analog                 11552  0
gameport               14824  1 analog
snd_mpu401              6312  0
snd_mpu401_uart         7296  1 snd_mpu401
snd_rawmidi            24704  1 snd_mpu401_uart
snd_seq_device          8460  1 snd_rawmidi
floppy                 59124  0
pcspkr                  3396  0
rtc                    12344  0
usblp                  12640  0
pcilynx                18792  0
ieee1394              100792  1 pcilynx
i2c_algo_bit            9416  1 pcilynx
shpchp                 96996  0
pci_hotplug            27508  1 shpchp
snd_intel8x0           33248  0
snd_ac97_codec         83932  1 snd_intel8x0
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  1 snd_pcm
snd                    54884  10 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc         10600  2 snd_intel8x0,snd_pcm
i2c_nforce2             6688  0
i2c_core               21200  4 i2c_acpi_ec,pcilynx,i2c_algo_bit,i2c_nforce2
amd64_agp              12232  0
agpgart                34792  2 nvidia,amd64_agp
ext3                  136264  1
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
dm_mod                 57692  1
evdev                   9664  0
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  1
lp                     12292  0
parport                35912  2 parport_pc,lp
md                     45584  0
reiserfs              262320  2
thermal                13000  0
processor              22812  1 thermal
fan                     4484  0
usbhid                 35264  0
forcedeth              21504  0
usbcore               118044  5 ehci_hcd,ohci_hcd,usblp,usbhid
ide_cd                 41572  1
cdrom                  39616  1 ide_cd
ide_disk               18464  6
ide_generic             1376  0
sata_nv                 9316  0
libata                 53764  1 sata_nv
scsi_mod              135688  2 sd_mod,libata
amd74xx                13948  1
ide_core              138772  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   26896  225
vesafb                  7992  0
capability              4712  0
commoncap               6816  1 capability
vga16fb                12584  1
vgastate                9664  1 vga16fb
softcursor              2272  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3872  2 vesafb,vga16fb
cfbcopyarea             4608  2 vesafb,vga16fb
fbcon                  38496  74
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon

```
Oh my motherboard is a "Asus K8N-E with nforce3 250GB chipset"

---

