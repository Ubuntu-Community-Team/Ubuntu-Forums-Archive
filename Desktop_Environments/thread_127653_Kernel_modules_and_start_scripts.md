---
title: "Kernel modules and start scripts"
date: 2006-02-09
forum: Desktop Environments
---

### Post by Pollastre on 2006-02-09
Hi , i'm trying to don't load some modules like bluetooth or ipv6 in my kubuntu , i was looking on /etc/modules but it only has 4 modules , after i see /etc/hotplug/blacklist and i add these lines to the file :

```

#Mios
ipv6
bluetooth
joydev
tsdev
hotkey
rfcomm
joydev
hotkey
8139cp
tc1100_wmi
lp
parport
parport_pc
md

``` 

Because i don't need load these modules , but  when i restart the sistem it still are loaded , it don't skip all of them for example ipv6 is removed but bluetooth  isn't . Why ?  are there other files to control loaded modules?

```

root@zero:~# lsmod
Module                  Size  Used by
ipv6                  217408  6
af_packet              20232  2
bluetooth              43012  0
i915                   17920  1
drm                    58004  2 i915
speedstep_centrino      7380  1
cpufreq_powersave       1920  0
cpufreq_stats           5124  0
cpufreq_userspace       4444  1
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
pcmcia                 24584  2
tc1100_wmi              6916  0
video                  16004  0
battery                 9604  0
container               4608  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
pcc_acpi               11392  0
sony_acpi               5516  0
ac                      4996  0
dev_acpi               11396  0
hotkey                  9508  0
sg                     33696  0
sr_mod                 15652  0
cdrom                  33952  1 sr_mod
tsdev                   7616  0
psmouse                26116  0
rtc                    11832  0
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
ohci1394               30644  0
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
hw_random               5268  0
snd_hda_intel          15872  1
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm
intel_agp              21276  1
agpgart                32328  3 drm,intel_agp
dm_mod                 50364  1
evdev                   9088  1
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
mousedev               10912  1
md                     40656  0
reiserfs              217200  1
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
usbhid                 30688  0
8139cp                 18432  0
8139too                23552  0
mii                     5248  2 8139cp,8139too
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  4 usbhid,ehci_hcd,uhci_hcd
sd_mod                 17424  3
ide_generic             1664  0
ide_core              125268  1 ide_generic
ata_piix                9476  6
ahci                   11268  0
libata                 47876  2 ata_piix,ahci
scsi_mod              124872  6 sg,sr_mod,sbp2,sd_mod,ahci,libata
unix                   24624  288
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
root@zero:~#      

```

Also when the system starts it say that is loading some stuff like Raid devices suport , or ntp clock , and i dont have neither of these on /etc/rc2./ from where is load it.
 
Where i can found doc about Ubuntu/Kubuntu starting modules and system services ?

Thanks :KS

---

