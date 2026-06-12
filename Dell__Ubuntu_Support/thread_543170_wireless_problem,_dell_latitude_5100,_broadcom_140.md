---
title: "wireless problem, dell latitude 5100, broadcom 1400"
date: 2007-09-04
forum: Dell  Ubuntu Support
---

### Post by ircarrascal on 2007-09-04
So I see lots of people have wireless problems; hopefully someone can help me. I have a Dell laptop Inspiron 5100 and my wireless card is a Broadcom 1400, which works fine in Windows. Since it didn't work in Ubuntu I tried to follow several methods I found online to make it work (installing drivers and such). I was able to see the Wireless link in System--Administration--Network, but now I can't. Something happened when I was trying to make it work such that the device just disappeared! I used to be able to see it after "lspci" but now it's not there anymore. Is it possible to 'disconnect' the wireless card from Ubuntu in this way? I guess it is I just don't know how I did it! But more important, can anybody tell me how to make it come back? Thanks, -Ivan.

---

### Post by coffecup1978 on 2007-09-04
I was struggling with a crappy Broadcom chip as well on my D600

there is a very good guide on [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

If the driver module gets unloaded from the kernel, lspci may not see it I think... did you reboot?

give us an lsmod to see what modules you have loaded...

---

### Post by ircarrascal on 2007-09-05
Well I saw the link and I tried 
> sudo ifconfig wlan0 up
as suggested but I got this error:
wlan0: ERROR while getting interface flags: No such device

lsmod gives this:

Module                  Size  Used by
wlan                  204868  0 
usbhid                 26592  0 
hid                    27392  1 usbhid
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ipv6                  268960  8 
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
speedstep_lib           6148  0 
cpufreq_ondemand        9228  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
sony_acpi               6284  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
ac                      6020  0 
button                  8720  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
container               5248  0 
battery                10756  0 
video                  16388  0 
dock                   10268  0 
nls_utf8                3072  1 
ntfs                  107764  1 
ndiswrapper           188252  0 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_intel8x0           34332  4 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
joydev                 10816  0 
snd_pcm                79876  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
pcmcia                 39212  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
snd                    54020  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
psmouse                38920  0 
serio_raw               7940  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
intel_agp              26140  1 
agpgart                35400  2 drm,intel_agp
af_packet              23816  4 
evdev                  11008  4 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  4 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
ata_generic             9092  0 
ata_piix               15492  3 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  5 sbp2,sg,sd_mod,sr_mod,libata
ehci_hcd               34188  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
b44                    28044  0 
mii                     6528  1 b44
generic                 5124  0 [permanent]
uhci_hcd               25360  0 
usbcore               134280  5 usbhid,ndiswrapper,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

lspci still doesn't show any wireless. Thanks for helping!

---

### Post by ircarrascal on 2007-09-05
Just to add something ... I can see the wireless device if I use the live CD.

---

