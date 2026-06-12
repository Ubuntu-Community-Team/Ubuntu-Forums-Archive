---
title: "Bluetooth mouse doesn't work after hibernation"
date: 2006-08-05
forum: Desktop Environments
---

### Post by cri on 2006-08-05
Hello, 

I'm running Kubuntu on a Dell 1405e. After a normal boot, I can use my bluetooth mouse just fine. I can hibernate the machine just fine too. However, whenever I resume from hibernation, my bluetooth mouse doesn't work. 90% of the time I end up rebooting to fix the problem, which kind of defeats the purpose of hibernating. 

Which service do I have to restart to restart the bluetooth subsystem? I've tried restarting the bluez-utils service but that does nothing. Anyone have a clue as to how to fix this?

Note that the mouse works fine when the machine resumes from suspend. 

Thanks!

---

### Post by philippe_carlo on 2006-08-05
You should try this once:
```

sudo rmmod bluetooth
sudo modprobe bluetooth

```

If your mouse needs kernel drivers too, just append the name of those to the commands above.

---

### Post by cri on 2006-08-05
Thanks for the tip! Unfortunately there are too many dependencies. When I `rmmod bluetooth` I get: 

"ERROR: Module bluetooth is in use by rfcomm,hidp,l2cap,hci_usb"

If I try to rmmod those modules they also fail because of dependencies. 

There has got to be an easier way. Is there a file I can use to configure how hibernation resumes?

---

### Post by 5-HT on 2006-08-05
You could try adding the bluetooth module to the MODULES= line in /etc/default/acpi-support. Any module listed on that line will be removed before suspend and reloaded on resume (should work for both suspend to disk [hibernation] and suspend to ram).

You may need to play around with adding some of those other modules as well, but maybe just bluetooth will do it?

---

### Post by cri on 2006-08-06
"You could try adding the bluetooth module to the MODULES= line in /etc/default/acpi-support."

No luck :( Exact same behavior. Below is my list of loaded modules, I don't see anything other than bluetooth that would be relevant. 

Module                  Size  Used by
i915                   21664  1
drm                    78484  2 i915
rfcomm                 43604  6
hidp                   33856  3
l2cap                  28192  14 rfcomm,hidp
ipv6                  286912  22
ppdev                   9668  0
speedstep_centrino      8752  1
cpufreq_userspace       6496  1
cpufreq_stats           6688  0
freq_table              4928  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  2 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               22848  1 i2c_acpi_ec
ndiswrapper           186320  0
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   14496  1
fat                    55548  1 vfat
dm_mod                 63256  1
md_mod                 76052  0
af_packet              24520  6
arc4                    2048  1
ieee80211_crypt_wep     5280  1
sbp2                   24996  0
parport_pc             37988  0
lp                     12356  0
parport                39400  3 ppdev,parport_pc,lp
snd_hda_intel          20468  1
snd_hda_codec         150768  1 snd_hda_intel
joydev                 10432  0
tsdev                   8032  0
ipw3945               132124  1
hci_usb                18004  7
snd_pcm_oss            56448  0
sdhci                  16096  0
snd_mixer_oss          20544  1 snd_pcm_oss
b44                    27980  0
mmc_core               31816  1 sdhci
mii                     6176  1 b44
ieee80211              38920  1 ipw3945
ieee80211_crypt         6528  2 ieee80211_crypt_wep,ieee80211
snd_pcm                96676  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
bluetooth              54084  16 rfcomm,hidp,l2cap,hci_usb
ieee80211_1_1_13       39880  0
ieee80211_1_1_13_crypt     7040  1 ieee80211_1_1_13
snd_timer              26884  1 snd_pcm
snd                    60004  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
serio_raw               7748  0
pcspkr                  2244  0
intel_agp              24700  1
agpgart                36784  3 drm,intel_agp
hw_random               5716  0
psmouse                40036  0
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm
sg                     40096  0
sr_mod                 17988  0
evdev                  10176  2
cdrom                  41408  1 sr_mod
ext3                  148104  1
jbd                    65876  1 ext3
ide_generic             1504  0
ohci1394               37524  0
ieee1394              306520  2 sbp2,ohci1394
ehci_hcd               33800  0
uhci_hcd               35408  0
usbcore               137700  5 ndiswrapper,hci_usb,ehci_hcd,uhci_hcd
sd_mod                 20448  4
generic                 5124  0
ata_piix               11364  7
libata                 83376  1 ata_piix
scsi_mod              145960  5 sbp2,sg,sr_mod,sd_mod,libata
thermal                13768  1
processor              26344  2 speedstep_centrino,thermal
fan                     4836  1
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

---

