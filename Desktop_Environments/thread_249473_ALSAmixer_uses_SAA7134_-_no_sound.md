---
title: "ALSAmixer uses SAA7134 - no sound"
date: 2006-09-02
forum: Desktop Environments
---

### Post by jenik on 2006-09-02
Hi, 

I've recently upgraded to Dapper and all sound stopped working. Volume controls in gnome and alsamixer are fine but noticed that alsamixer uses SAA7134 driver/soundcard while my SB Audigy LS uses the ca0106 driver. could that be the problem? how do i tell alsa to use the right soundcard?

thanks

jan

here's lsmod output if that helps

Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
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
nls_iso8859_1           4224  2
nls_cp437               5888  2
vfat                   13440  2
fat                    53020  1 vfat
reiserfs              268016  1
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
lp                     11844  0
rsrc_nonstatic         13440  0
pcmcia_core            42640  1 rsrc_nonstatic
saa7134_alsa           13408  2
saa7134               115936  1 saa7134_alsa
video_buf              22148  2 saa7134_alsa,saa7134
v4l2_common             6016  1 saa7134
v4l1_compat            14468  1 saa7134
ir_kbd_i2c              8460  1 saa7134
parport_pc             35780  1
ir_common               9988  2 saa7134,ir_kbd_i2c
snd_ca0106             34212  2
videodev                9856  1 saa7134
snd_rawmidi            25504  1 snd_ca0106
snd_seq_device          8716  1 snd_rawmidi
snd_ac97_codec         93088  1 snd_ca0106
snd_pcm_oss            53664  0
snd_mixer_oss          18688  4 snd_pcm_oss
snd_pcm                89864  4 saa7134_alsa,snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
parport                36296  3 ppdev,lp,parport_pc
snd                    55268  11 saa7134_alsa,snd_ca0106,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  4 snd
snd_ac97_bus            2304  1 snd_ac97_codec
snd_page_alloc         10632  2 snd_ca0106,snd_pcm
tsdev                   8000  0
floppy                 62148  0
nvidia               4550772  12
agpgart                34888  1 nvidia
pcspkr                  2180  0
rtc                    13492  0
psmouse                36100  0
serio_raw               7300  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
i2c_nforce2             6912  0
i2c_core               21904  5 i2c_acpi_ec,saa7134,ir_kbd_i2c,nvidia,i2c_nforce2
ipv6                  265728  10
sg                     37920  0
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
usb_storage            74176  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
forcedeth              30732  0
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130692  4 usb_storage,ehci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
generic                 5124  0
amd74xx                15260  0 [permanent]
sd_mod                 19984  6
sata_nv                 9732  10
libata                 78992  1 sata_nv
scsi_mod              139496  6 sr_mod,sbp2,sg,usb_storage,sd_mod,libata
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

---

### Post by jenik on 2006-10-19
anyone any idea?

---

