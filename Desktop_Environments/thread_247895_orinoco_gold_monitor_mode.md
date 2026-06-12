---
title: "orinoco gold monitor mode"
date: 2006-08-31
forum: Desktop Environments
---

### Post by bigodines on 2006-08-31
I'm trying to put my pcmcia orinoco gold into monitor mode but cant get this working.

I've already downloaded this driver [ [http://savannah.nongnu.org/cvs/?group=orinoco](http://savannah.nongnu.org/cvs/?group=orinoco) ] from cvs and installed. It didn't work when I put the card so I tried to rmmod hostap_cs and tried again. didn't work. Now, when I get eth2 down and up again, dmesg says:

> [17182888.396000] ADDRCONF(NETDEV_UP): eth2: link is not ready


lsmod says:
> Module                  Size  Used by
hci_usb                16660  0
hostap                119428  0
orinoco_cs             17800  1
orinoco                48148  1 orinoco_cs
hermes                  6272  1 orinoco_cs
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  5 hci_usb,rfcomm,l2cap
ppdev                   9220  0
fglrx                 394284  8
ipv6                  265728  8
speedstep_centrino      8400  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_centrino,cpufreq_stats
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
i2c_core               21904  1 i2c_acpi_ec
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
scsi_mod              139496  2 sr_mod,sbp2
lp                     11844  0
af_packet              22920  4
pcmcia                 40508  1 orinoco_cs
yenta_socket           28428  3
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
joydev                 10048  0
sdhci                  14848  0
mmc_core               30104  1 sdhci
ipw2200               107308  0
ieee80211              37064  1 ipw2200
ieee80211_crypt         6272  2 hostap,ieee80211
ieee80211_1_1_13       38216  0
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
tg3                   101764  0
pcspkr                  2180  0
rtc                    13492  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
snd_intel8x0           33692  4
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
snd_pcm                89864  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
psmouse                36100  0
snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
serio_raw               7300  0
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  2 fglrx,intel_agp
evdev                   9856  2
tsdev                   8000  0
ext3                  135688  2
jbd                    58772  1 ext3
usbhid                 39904  0
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0
uhci_hcd               33680  0
usbcore               130692  5 hci_usb,usbhid,ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  4
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  2 speedstep_centrino,thermal
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


does anyone get this thing working well? I've found many posts here in the forum but none of them seemed to work for me :(

sorry about my english.

---

