---
title: "hibernate doesn't work on precise"
date: 2012-05-06
forum: Desktop Environments
---

### Post by GOwin on 2012-05-06
Hibernate works fine in 10.04, the previous version installed in this computer.  I read that it's disabled by default, but after [re-enabling it](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html) hibernate still doesn't work.

My swap space is bigger than my RAM. 


Any idea who got this working?

---

### Post by Toz on 2012-05-06
Please provide some more information about your computer: 
- make
- model

...the results of this command:
```
cat /proc/cmdline
```

...and post back the contents of **/var/log/pm-suspend.log**

---

### Post by GOwin on 2012-05-06
It's a laptop from MSI model S270.

```
BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=30293492-926a-48bf-918d-64a483e79b8f ro quiet splash vt.handoff=7
```

I also tried tuxonice and it appeared like it was saving the computer state to the disk but somehow it wasn't restoring it back.

from the suspend log
```

Initial commandline parameters: 
Sat May  5 23:19:56 PHT 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux frankeinstein 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
dm_crypt               23125  1 
snd_atiixp             20001  3 
snd_atiixp_modem       19108  1 
snd_ac97_codec        134826  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                97188  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
msi_laptop             15055  0 
arc4                   12529  2 
sparse_keymap          13890  1 msi_laptop
rt2500pci              27646  0 
rt2x00pci              14577  1 rt2500pci
snd_seq_midi_event     14899  1 snd_seq_midi
rt2x00lib              55301  2 rt2500pci,rt2x00pci
parport_pc             32866  0 
rfcomm                 47604  4 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
ppdev                  17113  0 
mac80211              506816  2 rt2x00pci,rt2x00lib
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 49310  0 
psmouse                87692  0 
snd                    78855  16 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              205544  2 rt2x00lib,mac80211
yenta_socket           28084  0 
edac_core              53746  0 
pcmcia_rsrc            18430  1 yenta_socket
serio_raw              13211  0 
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
eeprom_93cx6           12725  1 rt2500pci
joydev                 17693  0 
k8temp                 13057  0 
edac_mce_amd           23709  0 
soundcore              15091  1 snd
snd_page_alloc         18529  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4              13301  0 
shpchp                 37277  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
radeon                804372  2 
usbhid                 47199  0 
ttm                    76949  1 radeon
8139too                32177  0 
firewire_ohci          41000  0 
hid                    99559  1 usbhid
drm_kms_helper         46978  1 radeon
drm                   242038  4 radeon,ttm,drm_kms_helper
8139cp                 27409  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
pata_atiixp            13204  4 
i2c_algo_bit           13423  1 radeon
             total       used       free     shared    buffers     cached
Mem:       1405852    1194084     211768          0      69588     460024
-/+ buffers/cache:     664472     741380
Swap:      1952764          0    1952764

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_vendor: No such file or directory
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Sat May  5 23:19:59 PHT 2012: performing hibernate
Initial commandline parameters: 
Sat May  5 23:29:36 PHT 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux frankeinstein 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 47604  4 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
dm_crypt               23125  1 
snd_atiixp_modem       19108  1 
snd_atiixp             20001  3 
snd_ac97_codec        134826  2 snd_atiixp_modem,snd_atiixp
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                97188  3 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
msi_laptop             15055  0 
sparse_keymap          13890  1 msi_laptop
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
rt2500pci              27646  0 
rt2x00pci              14577  1 rt2500pci
rt2x00lib              55301  2 rt2500pci,rt2x00pci
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              506816  2 rt2x00pci,rt2x00lib
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 49310  0 
cfg80211              205544  2 rt2x00lib,mac80211
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
snd                    78855  16 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87692  0 
joydev                 17693  0 
edac_core              53746  0 
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              13211  0 
eeprom_93cx6           12725  1 rt2500pci
soundcore              15091  1 snd
k8temp                 13057  0 
snd_page_alloc         18529  3 snd_atiixp_modem,snd_atiixp,snd_pcm
edac_mce_amd           23709  0 
i2c_piix4              13301  0 
shpchp                 37277  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
radeon                804372  2 
usbhid                 47199  0 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
8139too                32177  0 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
hid                    99559  1 usbhid
drm                   242038  4 radeon,ttm,drm_kms_helper
crc_itu_t              12707  1 firewire_core
pata_atiixp            13204  4 
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
8139cp                 27409  0 
i2c_algo_bit           13423  1 radeon
             total       used       free     shared    buffers     cached
Mem:       1405852    1232324     173528          0      72980     436472
-/+ buffers/cache:     722872     682980
Swap:      1952764          0    1952764

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_vendor: No such file or directory
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Sat May  5 23:29:40 PHT 2012: performing hibernate
Initial commandline parameters: --quirk-dpms-on
Sun May  6 00:33:28 PHT 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux frankeinstein 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 47604  4 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
dm_crypt               23125  1 
snd_atiixp             20001  3 
snd_atiixp_modem       19108  1 
snd_ac97_codec        134826  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                97188  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13324  0 
msi_laptop             15055  0 
snd_rawmidi            30748  1 snd_seq_midi
sparse_keymap          13890  1 msi_laptop
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
rt2500pci              27646  0 
rt2x00pci              14577  1 rt2500pci
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
rt2x00lib              55301  2 rt2500pci,rt2x00pci
mac80211              506816  2 rt2x00pci,rt2x00lib
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 49310  0 
joydev                 17693  0 
psmouse                87692  0 
snd                    78855  16 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13211  0 
cfg80211              205544  2 rt2x00lib,mac80211
yenta_socket           28084  0 
edac_core              53746  0 
pcmcia_rsrc            18430  1 yenta_socket
eeprom_93cx6           12725  1 rt2500pci
sdhci_pci              18826  0 
soundcore              15091  1 snd
edac_mce_amd           23709  0 
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         18529  3 snd_atiixp,snd_atiixp_modem,snd_pcm
k8temp                 13057  0 
i2c_piix4              13301  0 
shpchp                 37277  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
8139too                32177  0 
firewire_ohci          41000  0 
hid                    99559  1 usbhid
radeon                804372  2 
ttm                    76949  1 radeon
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci                  33205  1 sdhci_pci
8139cp                 27409  0 
pata_atiixp            13204  4 
drm_kms_helper         46978  1 radeon
drm                   242038  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
             total       used       free     shared    buffers     cached
Mem:       1405852    1133032     272820          0      19652     329548
-/+ buffers/cache:     783832     622020
Swap:      1952764       8920    1943844

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_vendor: No such file or directory
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Sun May  6 00:33:34 PHT 2012: performing hibernate
Initial commandline parameters: 
Sun May  6 19:39:12 PHT 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux frankeinstein 3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18281  2 
rfcomm                 47604  4 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
dm_crypt               23125  1 
snd_atiixp             20001  3 
snd_atiixp_modem       19108  1 
snd_ac97_codec        134826  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                97188  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12529  2 
joydev                 17693  0 
snd                    78855  16 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia                 49310  0 
rt2500pci              27646  0 
rt2x00pci              14577  1 rt2500pci
rt2x00lib              55301  2 rt2500pci,rt2x00pci
mac80211              506816  2 rt2x00pci,rt2x00lib
msi_laptop             15055  0 
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                87692  0 
soundcore              15091  1 snd
snd_page_alloc         18529  3 snd_atiixp,snd_atiixp_modem,snd_pcm
cfg80211              205544  2 rt2x00lib,mac80211
edac_core              53746  0 
k8temp                 13057  0 
serio_raw              13211  0 
sparse_keymap          13890  1 msi_laptop
eeprom_93cx6           12725  1 rt2500pci
edac_mce_amd           23709  0 
mac_hid                13253  0 
i2c_piix4              13301  0 
shpchp                 37277  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
sdhci_pci              18826  0 
firewire_ohci          41000  0 
8139too                32177  0 
hid                    99559  1 usbhid
radeon                804372  2 
firewire_core          63558  1 firewire_ohci
sdhci                  33205  1 sdhci_pci
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
drm                   242038  4 radeon,ttm,drm_kms_helper
8139cp                 27409  0 
crc_itu_t              12707  1 firewire_core
pata_atiixp            13204  4 
i2c_algo_bit           13423  1 radeon
             total       used       free     shared    buffers     cached
Mem:       1405852     595836     810016          0       7528     133064
-/+ buffers/cache:     455244     950608
Swap:      1952764     124668    1828096

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Daemon not responding.
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_vendor: No such file or directory
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Sun May  6 19:39:33 PHT 2012: performing hibernate
Initial commandline parameters: 
Mon May  7 08:14:30 PHT 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux frankeinstein 3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
dm_crypt               23125  1 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
snd_atiixp_modem       19108  1 
snd_atiixp             20001  3 
snd_ac97_codec        134826  2 snd_atiixp_modem,snd_atiixp
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                97188  3 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
msi_laptop             15055  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 47604  4 
bnep                   18281  2 
sparse_keymap          13890  1 msi_laptop
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
arc4                   12529  2 
joydev                 17693  0 
rt2500pci              27646  0 
rt2x00pci              14577  1 rt2500pci
rt2x00lib              55301  2 rt2500pci,rt2x00pci
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              506816  2 rt2x00pci,rt2x00lib
pcmcia                 49310  0 
psmouse                87692  0 
snd                    78855  16 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              205544  2 rt2x00lib,mac80211
edac_core              53746  0 
serio_raw              13211  0 
soundcore              15091  1 snd
k8temp                 13057  0 
edac_mce_amd           23709  0 
eeprom_93cx6           12725  1 rt2500pci
snd_page_alloc         18529  3 snd_atiixp_modem,snd_atiixp,snd_pcm
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_piix4              13301  0 
shpchp                 37277  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
radeon                804372  2 
usbhid                 47199  0 
8139too                32177  0 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
firewire_ohci          41000  0 
hid                    99559  1 usbhid
drm                   242038  4 radeon,ttm,drm_kms_helper
firewire_core          63558  1 firewire_ohci
i2c_algo_bit           13423  1 radeon
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
8139cp                 27409  0 
pata_atiixp            13204  4 
             total       used       free     shared    buffers     cached
Mem:       1405852    1100500     305352          0      76112     516048
-/+ buffers/cache:     508340     897512
Swap:      1952764          0    1952764

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_vendor: No such file or directory
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Mon May  7 08:14:34 PHT 2012: performing hibernate
Mon May  7 08:14:42 PHT 2012: Awake.
Mon May  7 08:14:42 PHT 2012: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Mon May  7 08:14:47 PHT 2012: Finished.


```

---

### Post by Toz on 2012-05-07
According to the log file, the last hibernate attempt worked (hibernate followed by thaw). The previous ones didn't - looks like you were trying some quirks for some of them. Can you confirm whether your last attempt worked or not?

Is tuxonice still installed? Or have you reverted to pm-utils?

Lets get a fresh log file and try hibernate again:
```
sudo mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
sudo pm-hibernate
```
...and post back whether it worked or not and the contents of the /var/log/pm-suspend.log file. Also, if it didn't work, can you describe what happens and how you recover?

And can you post back the results of the following commands:
```
lsmod
cat /etc/fstab
```

---

### Post by GOwin on 2012-05-07
Thank you Toz for staying with me on this.  Yes, I did try some other things but has removed TuxOnIce, which also failed to work for me.

I tried it again after clearing the old log. The shutdown process took longer than usual (i.e. compared to complete shutdown), so it must have been trying to save the state of computer. When I switched on the computer, it didn't resume from last time. And I noticed that my audio was muted, when it wasn't before.

suspend.log:
```

Initial commandline parameters: 
Tue May  8 07:41:19 PHT 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux frankeinstein 3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18281  2 
rfcomm                 47604  4 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
dm_crypt               23125  1 
arc4                   12529  2 
snd_atiixp             20001  3 
snd_atiixp_modem       19108  1 
snd_ac97_codec        134826  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                97188  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13324  0 
rt2500pci              27646  0 
rt2x00pci              14577  1 rt2500pci
rt2x00lib              55301  2 rt2500pci,rt2x00pci
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              506816  2 rt2x00pci,rt2x00lib
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
pcmcia                 49310  0 
joydev                 17693  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           28084  0 
cfg80211              205544  2 rt2x00lib,mac80211
pcmcia_rsrc            18430  1 yenta_socket
msi_laptop             15055  0 
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                87692  0 
snd                    78855  16 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 13057  0 
serio_raw              13211  0 
sparse_keymap          13890  1 msi_laptop
soundcore              15091  1 snd
snd_page_alloc         18529  3 snd_atiixp,snd_atiixp_modem,snd_pcm
eeprom_93cx6           12725  1 rt2500pci
edac_core              53746  0 
edac_mce_amd           23709  0 
i2c_piix4              13301  0 
mac_hid                13253  0 
shpchp                 37277  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
radeon                804372  2 
usbhid                 47199  0 
8139too                32177  0 
firewire_ohci          41000  0 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
hid                    99559  1 usbhid
drm                   242038  4 radeon,ttm,drm_kms_helper
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
8139cp                 27409  0 
pata_atiixp            13204  4 
i2c_algo_bit           13423  1 radeon
             total       used       free     shared    buffers     cached
Mem:       1405852    1262808     143044          0      15972     450372
-/+ buffers/cache:     796464     609388
Swap:      1952764     194088    1758676

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_vendor: No such file or directory
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Tue May  8 07:41:27 PHT 2012: performing hibernate

```

lsmod
```

Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18281  2 
rfcomm                 47604  4 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
dm_crypt               23125  1 
snd_atiixp_modem       19108  1 
snd_atiixp             20001  3 
snd_ac97_codec        134826  2 snd_atiixp_modem,snd_atiixp
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                97188  3 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
joydev                 17693  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
msi_laptop             15055  0 
sparse_keymap          13890  1 msi_laptop
arc4                   12529  2 
rt2500pci              27646  0 
rt2x00pci              14577  1 rt2500pci
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2x00lib              55301  2 rt2500pci,rt2x00pci
mac80211              506816  2 rt2x00pci,rt2x00lib
snd                    78855  16 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87692  0 
pcmcia                 49310  0 
serio_raw              13211  0 
cfg80211              205544  2 rt2x00lib,mac80211
edac_core              53746  0 
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
soundcore              15091  1 snd
k8temp                 13057  0 
eeprom_93cx6           12725  1 rt2500pci
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
edac_mce_amd           23709  0 
snd_page_alloc         18529  3 snd_atiixp_modem,snd_atiixp,snd_pcm
i2c_piix4              13301  0 
shpchp                 37277  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
radeon                804372  2 
usbhid                 47199  0 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
8139too                32177  0 
firewire_ohci          41000  0 
hid                    99559  1 usbhid
drm                   242038  4 radeon,ttm,drm_kms_helper
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
8139cp                 27409  0 
pata_atiixp            13204  4 
i2c_algo_bit           13423  1 radeon

```

fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=30293492-926a-48bf-918d-64a483e79b8f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=14aadd9a-4675-4d6d-ae20-b68b66a85194 /home           ext4    defaults        0       2
# /opt was on /dev/sda7 during installation
UUID=b27dceef-9281-4b0e-bb28-2d865d1d760f /opt            ext4    defaults        0       2
# swap was on /dev/sda6 during installation
#UUID=c92a6c12-88ab-4ea3-a16a-57d9e03ba18f none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0


```

---

### Post by Toz on 2012-05-07
> When I switched on the computer, it didn't resume from last time.
Did it restart? Did it go through a boot startup and bring you back to the login sreen?

This in interesting in your /etc/fstab file:
> /dev/mapper/cryptswap1 none swap sw 0 0
You have an encrypted swap file. Hibernate doesn't work with encrypted swap files. Consider this: the key to decrypt the swap file (to get to the hibernate image) is encrypted.

What I don't understand though, is that according to your previous log file, it worked once??? Is the swap encryption new?

---

### Post by GOwin on 2012-05-07
> **Toz said:**
> Did it restart? Did it go through a boot startup and bring you back to the login sreen?

It shut down properly, if that's what you mean. There's a delay and a black screen before it shut down, and I assumed it was trying to save the state of the computer.

> **Toz said:**
> 
This in interesting in your /etc/fstab file:

You have an encrypted swap file. Hibernate doesn't work with encrypted swap files. Consider this: the key to decrypt the swap file (to get to the hibernate image) is encrypted.

What I don't understand though, is that according to your previous log file, it worked once??? Is the swap encryption new?

I have no idea why it's encrypted, and no it's not new. I thought it's only my /home partition that's encrypted.

Kinda weird to find it worked in the log files, because it never did. When I hibernate, it would appear to be saving something (because of the delay in the shutdown) but when I restart I get to the login screen and not to the password/screensaver screen I expect.

---

### Post by GOwin on 2012-05-07
This encrypted swap space is a surprise. When I checked it on gparted it's reported as "unknown".

Let me just reformat this swap space first and find out if this is the culprit. Will get back to you. 

Thanks.

---

### Post by Das Goat on 2012-05-07
I don't know if this is related, but Toz, you have helped me out before.

When I close the lid on my Toshiba L775D-S7132, then open the lid, it will not come back from the suspend. I am forced to press the power button.


Also, does anyone know why the sound is always muted when 12.04 starts up? Is this by design?

UPDATE:

I tride Toz's code:

sudo mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
sudo pm-hibernate

I guess it hibernates. The screen doesn't turn off and I have a cursor in the uperleft corner. It wouldn't do anything until I pressed the power button. It looked like it was booting up (GRUB and all), but it came back up wher eI left off, this forum included. I would take that as a hibernate, or is that a suspend? Either way it didn't complete.

Here is my log file:

/code

Module                  Size  Used by
parport_pc             32866  0 
rfcomm                 47604  0 
bnep                   18281  2 
ppdev                  17113  0 
bluetooth             180104  10 rfcomm,bnep
vesafb                 13844  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_codec_realtek   223867  1 
uvcvideo               72627  0 
snd_hda_codec_hdmi     32474  1 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
psmouse                87692  0 
serio_raw              13211  0 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
rtl8192ce              84826  0 
snd_hwdep              13668  1 snd_hda_codec
k10temp                13166  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111202  1 rtl8192ce
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              506816  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              205544  2 rtlwifi,mac80211
i2c_piix4              13301  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13890  0 
fglrx                3263886  109 
snd                    78855  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19596  0 
wmi                    19256  0 
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
ums_realtek            18248  0 
r8169                  62099  0 
uas                    18027  0 
pata_atiixp            13204  0 
usb_storage            49198  1 ums_realtek

/endcode

---

### Post by Das Goat on 2012-05-07
[QUOTE=Das Goat;11915904]I don't know if this is related, but Toz, you have helped me out before.

When I close the lid on my Toshiba L775D-S7132, then open the lid, it will not come back from the suspend. I am forced to press the power button.


Also, does anyone know why the sound is always muted when 12.04 starts up? Is this by design?

UPDATE:

I tride Toz's code:

sudo mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
sudo pm-hibernate

I guess it hibernates. The screen doesn't turn off and I have a cursor in the uperleft corner. It wouldn't do anything until I pressed the power button. It looked like it was booting up (GRUB and all), but it came back up wher eI left off, this forum included. I would take that as a hibernate, or is that a suspend? Either way it didn't complete.

Here is my log file:

[/code]

Module                  Size  Used by
parport_pc             32866  0 
rfcomm                 47604  0 
bnep                   18281  2 
ppdev                  17113  0 
bluetooth             180104  10 rfcomm,bnep
vesafb                 13844  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_codec_realtek   223867  1 
uvcvideo               72627  0 
snd_hda_codec_hdmi     32474  1 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
psmouse                87692  0 
serio_raw              13211  0 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
rtl8192ce              84826  0 
snd_hwdep              13668  1 snd_hda_codec
k10temp                13166  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111202  1 rtl8192ce
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              506816  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              205544  2 rtlwifi,mac80211
i2c_piix4              13301  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13890  0 
fglrx                3263886  109 
snd                    78855  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19596  0 
wmi                    19256  0 
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
ums_realtek            18248  0 
r8169                  62099  0 
uas                    18027  0 
pata_atiixp            13204  0 
usb_storage            49198  1 ums_realtek

[/code]

---

### Post by GOwin on 2012-05-07
I fixed the "unknown" and encrypted swap partition issue. 

Still not resuming (or hibernating) Here are the new logs.

**suspend.log**
```

Initial commandline parameters: 
Tue May  8 10:21:17 PHT 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux frankeinstein 3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 47604  4 
dm_crypt               23125  0 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
snd_atiixp             20001  3 
snd_atiixp_modem       19108  1 
snd_ac97_codec        134826  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                97188  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13324  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
snd_rawmidi            30748  1 snd_seq_midi
parport_pc             32866  0 
ppdev                  17113  0 
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
msi_laptop             15055  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13890  1 msi_laptop
rt2500pci              27646  0 
joydev                 17693  0 
rt2x00pci              14577  1 rt2500pci
rt2x00lib              55301  2 rt2500pci,rt2x00pci
snd_timer              29990  2 snd_pcm,snd_seq
pcmcia                 49310  0 
mac80211              506816  2 rt2x00pci,rt2x00lib
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
sdhci_pci              18826  0 
snd                    78855  16 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              205544  2 rt2x00lib,mac80211
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
psmouse                87692  0 
eeprom_93cx6           12725  1 rt2500pci
k8temp                 13057  0 
edac_core              53746  0 
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              15091  1 snd
serio_raw              13211  0 
edac_mce_amd           23709  0 
snd_page_alloc         18529  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4              13301  0 
shpchp                 37277  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
8139too                32177  0 
firewire_ohci          41000  0 
hid                    99559  1 usbhid
radeon                804372  2 
firewire_core          63558  1 firewire_ohci
ttm                    76949  1 radeon
crc_itu_t              12707  1 firewire_core
sdhci                  33205  1 sdhci_pci
8139cp                 27409  0 
pata_atiixp            13204  4 
drm_kms_helper         46978  1 radeon
drm                   242038  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
             total       used       free     shared    buffers     cached
Mem:       1405852    1336900      68952          0      33664     702904
-/+ buffers/cache:     600332     805520
Swap:      1958908        232    1958676

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_vendor: No such file or directory
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Tue May  8 10:21:22 PHT 2012: performing hibernate

```

**fstab**
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=30293492-926a-48bf-918d-64a483e79b8f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=14aadd9a-4675-4d6d-ae20-b68b66a85194 /home           ext4    defaults        0       2
# /opt was on /dev/sda7 during installation
UUID=b27dceef-9281-4b0e-bb28-2d865d1d760f /opt            ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=b71fbf5a-a67f-45cf-a264-cec8e1bf3cee none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0


```

---

### Post by GOwin on 2012-05-08
I was researching about cryptswap and the mystery of my unknown swap partition and it turns out that it's a requirement for encrypted home partitions.

Now that I've taken it out, does it make my encrypted home useless?

Right now, hibernate still isn't working for me.

---

### Post by mips on 2012-05-08
Post the output of the following here: 
```
sudo blkid
cat /etc/initramfs-tools/conf.d/resume
```

You created a new partition so I suspect you have mismatched UUIDs.

---

### Post by GOwin on 2012-05-08
> **mips said:**
> Post the output of the following here: 
```
sudo blkid
cat /etc/initramfs-tools/conf.d/resume
```

You created a new partition so I suspect you have mismatched UUIDs.

You're right, they don't match. So I updated it and tried to hibernate again.
Before the shutdown it appeared to be saving the data instead of just a blank screen but it didn't resume back.

here's the log:
```

Initial commandline parameters: 
Tue May  8 10:21:17 PHT 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux frankeinstein 3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 47604  4 
dm_crypt               23125  0 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
snd_atiixp             20001  3 
snd_atiixp_modem       19108  1 
snd_ac97_codec        134826  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                97188  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13324  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
snd_rawmidi            30748  1 snd_seq_midi
parport_pc             32866  0 
ppdev                  17113  0 
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
msi_laptop             15055  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13890  1 msi_laptop
rt2500pci              27646  0 
joydev                 17693  0 
rt2x00pci              14577  1 rt2500pci
rt2x00lib              55301  2 rt2500pci,rt2x00pci
snd_timer              29990  2 snd_pcm,snd_seq
pcmcia                 49310  0 
mac80211              506816  2 rt2x00pci,rt2x00lib
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
sdhci_pci              18826  0 
snd                    78855  16 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              205544  2 rt2x00lib,mac80211
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
psmouse                87692  0 
eeprom_93cx6           12725  1 rt2500pci
k8temp                 13057  0 
edac_core              53746  0 
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              15091  1 snd
serio_raw              13211  0 
edac_mce_amd           23709  0 
snd_page_alloc         18529  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4              13301  0 
shpchp                 37277  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
8139too                32177  0 
firewire_ohci          41000  0 
hid                    99559  1 usbhid
radeon                804372  2 
firewire_core          63558  1 firewire_ohci
ttm                    76949  1 radeon
crc_itu_t              12707  1 firewire_core
sdhci                  33205  1 sdhci_pci
8139cp                 27409  0 
pata_atiixp            13204  4 
drm_kms_helper         46978  1 radeon
drm                   242038  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
             total       used       free     shared    buffers     cached
Mem:       1405852    1336900      68952          0      33664     702904
-/+ buffers/cache:     600332     805520
Swap:      1958908        232    1958676

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_vendor: No such file or directory
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Tue May  8 10:21:22 PHT 2012: performing hibernate
Initial commandline parameters: 
Tue May  8 13:52:47 PHT 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux frankeinstein 3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 47604  4 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
dm_crypt               23125  0 
snd_atiixp             20001  3 
snd_atiixp_modem       19108  1 
snd_ac97_codec        134826  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                97188  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
joydev                 17693  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
msi_laptop             15055  0 
sparse_keymap          13890  1 msi_laptop
rt2500pci              27646  0 
rt2x00pci              14577  1 rt2500pci
rt2x00lib              55301  2 rt2500pci,rt2x00pci
pcmcia                 49310  0 
snd_timer              29990  2 snd_pcm,snd_seq
sdhci_pci              18826  0 
mac80211              506816  2 rt2x00pci,rt2x00lib
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              205544  2 rt2x00lib,mac80211
snd                    78855  16 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
psmouse                87692  0 
serio_raw              13211  0 
eeprom_93cx6           12725  1 rt2500pci
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
edac_core              53746  0 
soundcore              15091  1 snd
edac_mce_amd           23709  0 
snd_page_alloc         18529  3 snd_atiixp,snd_atiixp_modem,snd_pcm
k8temp                 13057  0 
i2c_piix4              13301  0 
mac_hid                13253  0 
shpchp                 37277  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
radeon                804372  2 
usbhid                 47199  0 
8139too                32177  0 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
firewire_ohci          41000  0 
hid                    99559  1 usbhid
drm                   242038  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci                  33205  1 sdhci_pci
8139cp                 27409  0 
pata_atiixp            13204  4 
             total       used       free     shared    buffers     cached
Mem:       1405852     957668     448184          0      25476     375564
-/+ buffers/cache:     556628     849224
Swap:      1958908     128968    1829940

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_vendor: No such file or directory
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Tue May  8 13:52:55 PHT 2012: performing hibernate
Initial commandline parameters: 
Tue May  8 20:18:26 PHT 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux frankeinstein 3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 47604  4 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
dm_crypt               23125  0 
snd_atiixp_modem       19108  1 
snd_atiixp             20001  3 
snd_ac97_codec        134826  2 snd_atiixp_modem,snd_atiixp
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                97188  3 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
msi_laptop             15055  0 
sparse_keymap          13890  1 msi_laptop
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
joydev                 17693  0 
rt2500pci              27646  0 
rt2x00pci              14577  1 rt2500pci
rt2x00lib              55301  2 rt2500pci,rt2x00pci
snd_timer              29990  2 snd_pcm,snd_seq
mac80211              506816  2 rt2x00pci,rt2x00lib
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 49310  0 
cfg80211              205544  2 rt2x00lib,mac80211
psmouse                87692  0 
snd                    78855  16 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           28084  0 
serio_raw              13211  0 
pcmcia_rsrc            18430  1 yenta_socket
eeprom_93cx6           12725  1 rt2500pci
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
edac_core              53746  0 
k8temp                 13057  0 
soundcore              15091  1 snd
edac_mce_amd           23709  0 
snd_page_alloc         18529  3 snd_atiixp_modem,snd_atiixp,snd_pcm
i2c_piix4              13301  0 
shpchp                 37277  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
radeon                804372  2 
usbhid                 47199  0 
ttm                    76949  1 radeon
firewire_ohci          41000  0 
sdhci_pci              18826  0 
8139too                32177  0 
firewire_core          63558  1 firewire_ohci
drm_kms_helper         46978  1 radeon
hid                    99559  1 usbhid
drm                   242038  4 radeon,ttm,drm_kms_helper
crc_itu_t              12707  1 firewire_core
8139cp                 27409  0 
sdhci                  33205  1 sdhci_pci
pata_atiixp            13204  4 
i2c_algo_bit           13423  1 radeon
             total       used       free     shared    buffers     cached
Mem:       1405852    1144440     261412          0      22764     292464
-/+ buffers/cache:     829212     576640
Swap:      1958908      12720    1946188

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_vendor: No such file or directory
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Tue May  8 20:18:33 PHT 2012: performing hibernate


```

---

### Post by mips on 2012-05-08
> **GOwin said:**
> You're right, they don't match. So I updated it and tried to hibernate again.


Did you update initramfs afterwards?
```
sudo update-initramfs -u
```

So the UUID from blkid now matches that of /etc/fstab & /etc/initramfs-tools/conf.d/resume for swap?

---

### Post by GOwin on 2012-05-08
> **mips said:**
> Did you update initramfs afterwards?
```
sudo update-initramfs -u
```

So the UUID from blkid now matches that of /etc/fstab & /etc/initramfs-tools/conf.d/resume for swap?

Nope but I just did that now and I get this:

cryptsetup: WARNING: failed to detect canonical device of /dev/dm-0

How important is this?

$ pm-hibernate now works!! yippee.

---

### Post by mips on 2012-05-08
> **GOwin said:**
> Nope but I just did that now and I get this:

cryptsetup: WARNING: failed to detect canonical device of /dev/dm-0

How important is this?

Anyway, pm-hibernate now works!! yippee. But I have a security issue, it returns me to my desktop's last state without asking for a password.

I'm lost now in all honesty but post the output of **cat /etc/crypttab**

Do you have any encrypted partitions? Or do you use LVM, **sudo dmsetup ls** ?

---

### Post by GOwin on 2012-05-08
> **mips said:**
> I'm lost now in all honesty but post the output of **cat /etc/crypttab**

Do you have any encrypted partitions?

this is my /etc/crypttab
```

cryptswap1 /dev/sda6 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

```

Yes, my /home partition is encrypted.

---

### Post by mips on 2012-05-08
> **GOwin said:**
> this is my /etc/crypttab
```

cryptswap1 /dev/sda6 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

```

Yes, my /home partition is encrypted.

Ok when it comes to encryption I'm clueless, hopefully someone else can figure out how to fix that problem.

Edit: also post output of **cat /etc/fstab**

---

### Post by GOwin on 2012-05-08
> **mips said:**
> Ok when it comes to encryption I'm clueless, hopefully someone else can figure out how to fix that problem.

Edit: also post output of **cat /etc/fstab**

I suppose this will have to be taken one step at a time. Thank you very much for helping me with the hibernation problem mips.

here's my fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=30293492-926a-48bf-918d-64a483e79b8f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=14aadd9a-4675-4d6d-ae20-b68b66a85194 /home           ext4    defaults        0       2
# /opt was on /dev/sda7 during installation
UUID=b27dceef-9281-4b0e-bb28-2d865d1d760f /opt            ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=b71fbf5a-a67f-45cf-a264-cec8e1bf3cee none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0


```

---

### Post by mips on 2012-05-08
If you look at your fstab you can see the swap partition was previously encrypted. You either need to restore the encryption for swap or figure out how to remove whatever remnants it left behind.

This is where I bow out though as any help I could offer would surely land you in more trouble and make myself very unpopular :biggrin:

Hope you come right.


> **GOwin said:**
> I suppose this will have to be taken one step at a time. Thank you very much for helping me with the hibernation problem mips.

here's my fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=30293492-926a-48bf-918d-64a483e79b8f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=14aadd9a-4675-4d6d-ae20-b68b66a85194 /home           ext4    defaults        0       2
# /opt was on /dev/sda7 during installation
UUID=b27dceef-9281-4b0e-bb28-2d865d1d760f /opt            ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=b71fbf5a-a67f-45cf-a264-cec8e1bf3cee none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0


```

---

### Post by Toz on 2012-05-08
@GOwin, the good news is that hibernate now works. And thanks to @mips for all his help and advice.

As for the encrypted swap remnants, have a look at this link: [http://www.logilab.org/blogentry/29155]("http://www.logilab.org/blogentry/29155"). I think you just need to remove that final remnant. 

I don't believe that an encrypted swap is necessary for an encrypted home, but its generally considered best practice to encrypt the swap if your in the need for encryption.

---

### Post by GOwin on 2012-05-08
> **Toz said:**
> @GOwin, the good news is that hibernate now works. And thanks to @mips for all his help and advice.

As for the encrypted swap remnants, have a look at this link: [http://www.logilab.org/blogentry/29155]("http://www.logilab.org/blogentry/29155"). I think you just need to remove that final remnant. 

I don't believe that an encrypted swap is necessary for an encrypted home, but its generally considered best practice to encrypt the swap if your in the need for encryption.

Thank you,too Toz.

---

