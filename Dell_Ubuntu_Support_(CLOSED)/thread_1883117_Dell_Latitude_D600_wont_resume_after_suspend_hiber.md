---
title: "Dell Latitude D600 wont resume after suspend hibernate"
date: 2011-11-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ken631 on 2011-11-18
Now I've searched for information regarding this model. I see there is another Dell wont resume after suspend thread but it had to do with a more recent model, although it is a very similar situation.

Close lid, shuts down or suspends, open lid, I hear the churning of the harddrive but visual.

Dell Lat D600
Intel pentium m 1.5 ghtz mobile processor
60 gig hard drive with 30 gig available.

Thanks

pm-suspend.log contents

Initial commandline parameters: 
Sun Nov 13 12:05:59 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kens-laptop 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  8 bnep,rfcomm
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               22565  0 
binfmt_misc            17292  1 
joydev                 17393  0 
ppdev                  12849  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
dcdbas                 14098  0 
arc4                   12473  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
b43legacy             131930  0 
pcmcia                 39822  0 
mac80211              272785  1 b43legacy
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
cfg80211              172392  2 b43legacy,mac80211
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
parport_pc             32114  1 
shpchp                 32356  0 
videodev               85626  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
radeon                925020  2 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192226  4 radeon,ttm,drm_kms_helper
usbhid                 41905  0 
hid                    77367  1 usbhid
tg3                   132972  0 
ssb                    50682  1 b43legacy
i2c_algo_bit           13199  1 radeon
video                  18908  0 
             total       used       free     shared    buffers     cached
Mem:       1025816     892736     133080          0      47992     432192
-/+ buffers/cache:     412552     613264
Swap:      1368060      26228    1341832

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:

/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Nov 13 12:06:06 EST 2011: performing suspend
Initial commandline parameters: 
Sun Nov 13 12:43:47 EST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux kens-laptop 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
binfmt_misc            17292  1 
dm_crypt               22565  0 
joydev                 17393  0 
ppdev                  12849  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
dcdbas                 14098  0 
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
pcmcia                 39822  0 
b43legacy             131930  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
mac80211              272785  1 b43legacy
snd_timer              28932  2 snd_pcm,snd_seq
cfg80211              172392  2 b43legacy,mac80211
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27428  0 
psmouse                73673  0 
pcmcia_rsrc            18367  1 yenta_socket
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32356  0 
parport_pc             32114  1 
videodev               85626  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
radeon                925020  2 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192226  4 radeon,ttm,drm_kms_helper
usbhid                 41905  0 
hid                    77367  1 usbhid
tg3                   132972  0 
ssb                    50682  1 b43legacy
i2c_algo_bit           13199  1 radeon
video                  18908  0 
             total       used       free     shared    buffers     cached
Mem:       1025816     854344     171472          0      90532     345180
-/+ buffers/cache:     418632     607184
Swap:      1368060      26140    1341920

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
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
Running hook /usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Sun Nov 13 12:43:53 EST 2011: performing hibernate
Sun Nov 13 12:44:55 EST 2011: Awake.
Sun Nov 13 12:44:55 EST 2011: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate:
method return sender=:1.90 -> dest=:1.88 reply_serial=2

/usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Sun Nov 13 12:45:11 EST 2011: Finished.

---

### Post by ken631 on 2011-11-18
Update

I turned off swap, and made some progress.  It now half resumes but hangs on long in screen, i see the top panel and mouse but the rest is black.  I still have to do alt+ctrl+bckspc to restart.

---

### Post by ken631 on 2011-11-20
Ok downloaded xubuntu desktop to try suspend hibernate on a different desktop and it seems to be a gnome issue.  Hibernate worked wonderful, suspend did not, that could be a hardware issue.  Will have to try it on kde

---

