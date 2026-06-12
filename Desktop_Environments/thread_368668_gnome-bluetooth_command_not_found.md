---
title: "gnome-bluetooth command not found"
date: 2007-02-23
forum: Desktop Environments
---

### Post by gary441 on 2007-02-23
Hello all,
I've been trying to connect a Motorola H500 and  Zoom 4310a  devices all day. 
When I do:
sudo btsco -i hci0 MAC-address-of-H500 1
I get:
Can't connect RFCOMM channel : Resource temporarily unavailble

Also when I try gnome-bluetooth, I get "bash: gnome-bluetooth: command not found"


Any ideas on either problem?


uname -a
laptop 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux
----------------------------------------------------------------

lsmod
Module                  Size  Used by
snd_bt_sco             17932  0
snd_hwdep              10756  1 snd_bt_sco
binfmt_misc            13448  1
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
ipv6                  272288  12
radeon                118816  2
drm                    74644  3 radeon
acpi_cpufreq            8644  0
speedstep_lib           5764  0
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  2 acpi_cpufreq,cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  1
cpufreq_conservative     8712  0
video                  17540  0
tc1100_wmi              8324  0
sbs                    16804  0
sony_acpi               6412  0
pcc_acpi               14080  0
i2c_ec                  6272  1 sbs
hotkey                 11556  0
dev_acpi               12292  0
button                  7952  0
battery                11652  0
container               5632  0
ac                      6788  0
asus_acpi              17688  0
sbp2                   24584  0
scsi_mod              144648  1 sbp2
lp                     12964  0
joydev                 11200  0
tsdev                   9152  0
hci_usb                18068  2
bluetooth              53476  7 rfcomm,l2cap,hci_usb
snd_ali5451            25356  1
snd_ac97_codec         97696  1 snd_ali5451
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
i2c_ali1535             7940  0
i2c_ali15x3             8708  0
pcmcia                 40380  0
psmouse                41352  0
snd_pcm                84612  4 snd_bt_sco,snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
i2c_core               23424  3 i2c_ec,i2c_ali1535,i2c_ali15x3
evdev                  11392  2
ati_agp                10636  1
agpgart                34888  2 drm,ati_agp
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
serio_raw               8452  0
snd                    58372  10 snd_bt_sco,snd_hwdep,snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_bt_sco,snd_pcm
ipw2200               115652  0
parport_pc             37796  1
parport                39496  2 lp,parport_pc
pcspkr                  4352  0
natsemi                30688  0
yenta_socket           28812  1
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211              35272  1 ipw2200
ieee80211_crypt         7552  1 ieee80211
ext3                  142856  1
jbd                    62228  1 ext3
ehci_hcd               34696  0
uhci_hcd               24968  0
usbcore               134912  4 hci_usb,ehci_hcd,uhci_hcd
ohci1394               37040  0
ieee1394              306104  2 sbp2,ohci1394
ide_generic             2432  0
ide_cd                 33696  0
cdrom                  38944  1 ide_cd
ide_disk               18560  3
generic                 6276  0
alim15x3               13324  0 [permanent]
thermal                15624  0
processor              31560  2 acpi_cpufreq,thermal
fan                     6020  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability
------------------------------------------------
hcitool dev
Devices:
        hci0    00:10:60:B2:DD:71
#this device is the Zoom

---

