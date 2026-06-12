---
title: "How do you wake a desktop computer from suspend?"
date: 2013-10-13
forum: Desktop Environments
---

### Post by sdowney717 on 2013-10-13
running ubuntu 12.04
what is the secret?
The video wont come back up, the box with the mb comes to life at least it makes whirring noises.
Running nvidia card
Somebody knows something I am sure.

---

### Post by Frogs Hair on 2013-10-13
I have always had depress the power button slightly to awaken my desktop computer. For an unknown  reason the mouse and keyboard have never worked to awaken the computer with Ubuntu installations, but do so on the Windows partition . I also run a Nvidia card and drivers default or otherwise have never made a difference. I have never tried to set up a key binding because the case/tower is easily reached . In my case, the entire system remains in suspend not just the monitor.

---

### Post by whitesmith on 2013-10-13
My system works as it should: any key press or mouse click will awaken the system. I suspect you're looking at a hardware problem that doesn't sound particularly easy to track down.

---

### Post by egeezer on 2013-10-13
Mine won't work on just any key - requires Enter.  Try the Enter after the power switch.

---

### Post by peter d on 2013-10-13
Power button works for me.

---

### Post by slickymaster on 2013-10-13
> **peter d said:**
> Power button works for me.

+1

---

### Post by rosswmcgee on 2013-10-13
I just press the right side enter key, works on several systems two ubuntu 12.04lts  one mint maya

---

### Post by sdowney717 on 2013-10-13
I looked into the logs and here they are

PM suspend log
```
Initial commandline parameters: 
Tue Jan  1 01:22:55 EST 2002: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux scott-MS-7104 3.2.0-44-generic #69-Ubuntu SMP Thu May 16 18:27:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
vesafb                 13516  1 
bnep                   17830  2 
rfcomm                 38139  0 
binfmt_misc            17292  1 
bluetooth             158479  10 bnep,rfcomm
nvidia              10286823  40 
snd_ice1724           107034  2 
snd_ice17xx_ak4xxx     13163  1 snd_ice1724
snd_ac97_codec        110213  1 snd_ice1724
ac97_bus               12642  1 snd_ac97_codec
snd_ak4xxx_adda        18464  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_ak4114             14326  1 snd_ice1724
snd_pt2258             12986  1 snd_ice1724
snd_i2c                13863  2 snd_ice1724,snd_pt2258
snd_ak4113             14307  1 snd_ice1724
arc4                   12473  2 
snd_pcm                80916  4 snd_ice1724,snd_ac97_codec,snd_ak4114,snd_ak4113
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_ice1724,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rt2800usb              22373  0 
rt2800lib              53298  1 rt2800usb
crc_ccitt              12627  1 rt2800lib
rt2x00usb              20099  1 rt2800usb
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17393  0 
rt2x00lib              48875  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436493  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178877  2 rt2x00lib,mac80211
snd                    62218  16 snd_ice1724,snd_ac97_codec,snd_ak4xxx_adda,snd_ak4114,snd_pt2258,snd_i2c,snd_ak4113,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  12849  0 
lm85                   22593  0 
usbhid                 41937  0 
psmouse                96718  0 
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
i2c_i801               17346  0 
serio_raw              13027  0 
hid                    77428  1 usbhid
parport_pc             32114  1 
intel_rng              12700  0 
cypress_m8             22832  0 
usbserial              37201  1 cypress_m8
hwmon_vid              12723  1 lm85
mac_hid                13077  0 
shpchp                 32265  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
floppy                 60184  0 
e100                   36289  0 
crc_itu_t              12627  1 firewire_core
e1000                 101795  0 
             total       used       free     shared    buffers     cached
Mem:       1024668     688704     335964          0      65868     375632
-/+ buffers/cache:     247204     777464
Swap:      1046524          0    1046524

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
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Jan  1 01:22:58 EST 2002: performing suspend
Initial commandline parameters: 
Tue Jan  1 00:03:10 EST 2002: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux scott-MS-7104 3.2.0-44-generic #69-Ubuntu SMP Thu May 16 18:27:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
usb_storage            39646  1 
rfcomm                 38139  0 
snd_ice1724           107034  2 
snd_ice17xx_ak4xxx     13163  1 snd_ice1724
snd_ac97_codec        110213  1 snd_ice1724
nvidia              10286823  40 
bnep                   17830  2 
ac97_bus               12642  1 snd_ac97_codec
bluetooth             158479  10 rfcomm,bnep
snd_ak4xxx_adda        18464  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_ak4114             14326  1 snd_ice1724
snd_pt2258             12986  1 snd_ice1724
snd_i2c                13863  2 snd_ice1724,snd_pt2258
snd_ak4113             14307  1 snd_ice1724
snd_pcm                80916  4 snd_ice1724,snd_ac97_codec,snd_ak4114,snd_ak4113
binfmt_misc            17292  1 
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_ice1724,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  16 snd_ice1724,snd_ac97_codec,snd_ak4xxx_adda,snd_ak4114,snd_pt2258,snd_i2c,snd_ak4113,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt2800usb              22373  0 
rt2800lib              53298  1 rt2800usb
crc_ccitt              12627  1 rt2800lib
rt2x00usb              20099  1 rt2800usb
rt2x00lib              48875  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436493  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178877  2 rt2x00lib,mac80211
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
ppdev                  12849  0 
usbhid                 41937  0 
hid                    77428  1 usbhid
shpchp                 32265  0 
cypress_m8             22832  0 
usbserial              37201  1 cypress_m8
parport_pc             32114  1 
lm85                   22593  0 
psmouse                96718  0 
i2c_i801               17346  0 
serio_raw              13027  0 
intel_rng              12700  0 
mac_hid                13077  0 
hwmon_vid              12723  1 lm85
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
e100                   36289  0 
floppy                 60184  0 
e1000                 101795  0 
             total       used       free     shared    buffers     cached
Mem:       1024668     705228     319440          0      66560     389428
-/+ buffers/cache:     249240     775428
Swap:      1046524          0    1046524

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
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Jan  1 00:03:12 EST 2002: performing suspend
Tue Jan  1 00:04:32 EST 2002: Awake.
Tue Jan  1 00:04:32 EST 2002: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Jan  1 00:04:34 EST 2002: Finished.
Initial commandline parameters: 
Tue Jan  1 00:11:33 EST 2002: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux scott-MS-7104 3.2.0-44-generic #69-Ubuntu SMP Thu May 16 18:27:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
vesafb                 13516  1 
nvidia              10286823  40 
arc4                   12473  2 
snd_ice1724           107034  2 
snd_ice17xx_ak4xxx     13163  1 snd_ice1724
snd_ac97_codec        110213  1 snd_ice1724
ac97_bus               12642  1 snd_ac97_codec
snd_ak4xxx_adda        18464  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_ak4114             14326  1 snd_ice1724
snd_pt2258             12986  1 snd_ice1724
snd_i2c                13863  2 snd_ice1724,snd_pt2258
snd_ak4113             14307  1 snd_ice1724
snd_pcm                80916  4 snd_ice1724,snd_ac97_codec,snd_ak4114,snd_ak4113
rt2800usb              22373  0 
rt2800lib              53298  1 rt2800usb
crc_ccitt              12627  1 rt2800lib
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_ice1724,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rt2x00usb              20099  1 rt2800usb
rt2x00lib              48875  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436493  3 rt2800lib,rt2x00usb,rt2x00lib
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cypress_m8             22832  0 
snd                    62218  16 snd_ice1724,snd_ac97_codec,snd_ak4xxx_adda,snd_ak4114,snd_pt2258,snd_i2c,snd_ak4113,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
psmouse                96718  0 
bnep                   17830  2 
rfcomm                 38139  0 
snd_page_alloc         14115  1 snd_pcm
cfg80211              178877  2 rt2x00lib,mac80211
bluetooth             158479  10 bnep,rfcomm
usbserial              37201  1 cypress_m8
ppdev                  12849  0 
serio_raw              13027  0 
binfmt_misc            17292  1 
parport_pc             32114  1 
lm85                   22593  0 
shpchp                 32265  0 
i2c_i801               17346  0 
intel_rng              12700  0 
hwmon_vid              12723  1 lm85
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            39646  0 
usbhid                 41937  0 
hid                    77428  1 usbhid
e100                   36289  0 
e1000                 101795  0 
floppy                 60184  0 
             total       used       free     shared    buffers     cached
Mem:       1024668     713408     311260          0      71228     385828
-/+ buffers/cache:     256352     768316
Swap:      1046524          0    1046524

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
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Jan  1 00:11:36 EST 2002: performing suspend
Tue Jan  1 00:13:07 EST 2002: Awake.
Tue Jan  1 00:13:07 EST 2002: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Jan  1 00:13:09 EST 2002: Finished.
```

---

### Post by sdowney717 on 2013-10-13
dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-44-generic (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #69-Ubuntu SMP Thu May 16 18:27:54 UTC 2013 (Ubuntu 3.2.0-44.69-generic 3.2.44)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe30000 (usable)
[    0.000000]  BIOS-e820: 000000003fe30000 - 000000003fe414a0 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fe414a0 - 000000003ff30000 (usable)
[    0.000000]  BIOS-e820: 000000003ff30000 - 000000003ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff40000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI:                  /S875WP1                        , BIOS WP87510A.86B.0059.P18.0502071117 02/07/2005
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3ff30 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfa000-1c00000
[    0.000000] RAMDISK: 364d8000 - 37264000
[    0.000000] ACPI: RSDP 000f61a0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3ff30000 00030 (v01 INTEL  S875PWP3 20050207 MSFT 00000097)
[    0.000000] ACPI: FACP 3ff30200 00081 (v02 INTEL  S875PWP3 20050207 MSFT 00000097)
[    0.000000] ACPI: DSDT 3ff30370 0424E (v01 INTEL  S875PWP3 00000001 MSFT 0100000D)
[    0.000000] ACPI: FACS 3ff40000 00040
[    0.000000] ACPI: APIC 3ff30300 00068 (v01 INTEL  S875PWP3 20050207 MSFT 00000097)
[    0.000000] ACPI: WDDT 3ff345c0 00040 (v01 INTEL  OEMWDDT  00000001 MSFT 0100000D)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 135MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003ff30
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fe30
[    0.000000]     0: 0x0003fe42 -> 0x0003ff30
[    0.000000] On node 0 totalpages: 261805
[    0.000000] free_area_init_node: node 0, pgdat c1829c00, node_mem_map f5cd8200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 271 pages used for memmap
[    0.000000]   HighMem zone: 34321 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:becf0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77dc000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259758
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-44-generic root=UUID=16ad197c-fcf8-416b-ae25-19216ab02320 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4190720 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003ff30)
[    0.000000] Memory: 1010080k/1047744k available (5632k kernel code, 37140k reserved, 2775k data, 716k init, 138368k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1837000 - 0xc18ea000   ( 716 kB)
[    0.000000]       .data : 0xc15802c4 - 0xc18362c0   (2775 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15802c4   (5632 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5808000 soft=f580a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2792.808 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5585.61 BogoMIPS (lpj=11171232)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.004041] Security Framework initialized
[    0.004069] AppArmor: AppArmor initialized
[    0.004073] Yama: becoming mindful.
[    0.004157] Mount-cache hash table entries: 512
[    0.004346] Initializing cgroup subsys cpuacct
[    0.004355] Initializing cgroup subsys memory
[    0.004367] Initializing cgroup subsys devices
[    0.004371] Initializing cgroup subsys freezer
[    0.004374] Initializing cgroup subsys blkio
[    0.004386] Initializing cgroup subsys perf_event
[    0.004429] CPU: Physical Processor ID: 0
[    0.004432] CPU: Processor Core ID: 0
[    0.004436] mce: CPU supports 4 MCE banks
[    0.004451] CPU0: Thermal monitoring enabled (TM1)
[    0.004456] using mwait in idle threads.
[    0.009301] ACPI: Core revision 20110623
[    0.012735] ftrace: allocating 25502 entries in 50 pages
[    0.016067] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016406] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.059377] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 04
[    0.060003] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.060003] ... version:                0
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      18
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             0000007fffffffff
[    0.060003] ... fixed-purpose events:   0
[    0.060003] ... event mask:             000000000003ffff
[    0.060003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.060003] CPU 1 irqstacks, hard=f58b0000 soft=f58b2000
[    0.060003] Booting Node   0, Processors  #1 Ok.
[    0.060003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.148046] NMI watchdog enabled, takes one hw-pmu counter.
[    0.148105] Brought up 2 CPUs
[    0.148111] Total of 2 processors activated (11172.07 BogoMIPS).
[    0.149144] devtmpfs: initialized
[    0.149144] EVM: security.selinux
[    0.149144] EVM: security.SMACK64
[    0.149144] EVM: security.capability
[    0.149144] PM: Registering ACPI NVS region at 3fe30000 (70816 bytes)
[    0.149144] PM: Registering ACPI NVS region at 3ff40000 (720896 bytes)
[    0.152310] print_constraints: dummy: 
[    0.152347] RTC time:  0:00:48, date: 01/01/02
[    0.152404] NET: Registered protocol family 16
[    0.152520] Trying to unpack rootfs image as initramfs...
[    0.152697] EISA bus registered
[    0.152762] ACPI: bus type pci registered
[    0.154231] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
[    0.154236] PCI: Using configuration type 1 for base access
[    0.168176] bio: create slab <bio-0> at 0
[    0.168375] ACPI: Added _OSI(Module Device)
[    0.168382] ACPI: Added _OSI(Processor Device)
[    0.168387] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.168393] ACPI: Added _OSI(Processor Aggregator Device)
[    0.170525] ACPI: EC: Look up EC in DSDT
[    0.173230] ACPI: Executed 2 blocks of module-level executable AML code
[    0.177851] ACPI: Interpreter enabled
[    0.177873] ACPI: (supports S0 S1 S3 S4 S5)
[    0.177927] ACPI: Using IOAPIC for interrupt routing
[    0.186423] ACPI: Power Resource [URP1] (off)
[    0.186529] ACPI: Power Resource [URP2] (off)
[    0.186633] ACPI: Power Resource [FDDP] (off)
[    0.186733] ACPI: Power Resource [LPTP] (off)
[    0.190565] ACPI: No dock devices found.
[    0.190571] HEST: Table not found.
[    0.190582] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.190732] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.191052] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.191061] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.191068] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.191075] pci_root PNP0A03:00: host bridge window [mem 0x40000000-0xffffffff] (ignored)
[    0.191101] pci 0000:00:00.0: [8086:2578] type 0 class 0x000600
[    0.191108] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
[    0.191123] pci 0000:00:00.0: reg 10: [mem 0xf4000000-0xf7ffffff pref]
[    0.191215] pci 0000:00:01.0: [8086:2579] type 1 class 0x000604
[    0.191269] pci 0000:00:03.0: [8086:257b] type 1 class 0x000604
[    0.191325] pci 0000:00:06.0: [8086:257e] type 0 class 0x000880
[    0.191343] pci 0000:00:06.0: reg 10: [mem 0xfecf0000-0xfecf0fff]
[    0.191452] pci 0000:00:1d.0: [8086:24d2] type 0 class 0x000c03
[    0.191512] pci 0000:00:1d.0: reg 20: [io  0xcc00-0xcc1f]
[    0.191562] pci 0000:00:1d.1: [8086:24d4] type 0 class 0x000c03
[    0.191624] pci 0000:00:1d.1: reg 20: [io  0xd000-0xd01f]
[    0.191679] pci 0000:00:1d.2: [8086:24d7] type 0 class 0x000c03
[    0.191739] pci 0000:00:1d.2: reg 20: [io  0xd400-0xd41f]
[    0.191789] pci 0000:00:1d.3: [8086:24de] type 0 class 0x000c03
[    0.191849] pci 0000:00:1d.3: reg 20: [io  0xd800-0xd81f]
[    0.191915] pci 0000:00:1d.7: [8086:24dd] type 0 class 0x000c03
[    0.191947] pci 0000:00:1d.7: reg 10: [mem 0xfebffc00-0xfebfffff]
[    0.192087] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.192097] pci 0000:00:1d.7: PME# disabled
[    0.192125] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.192189] pci 0000:00:1f.0: [8086:24d0] type 0 class 0x000601
[    0.192274] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.192310] pci 0000:00:1f.1: [8086:24db] type 0 class 0x000101
[    0.192332] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.192348] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.192364] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.192380] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.192395] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.192411] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.192454] pci 0000:00:1f.2: [8086:24d1] type 0 class 0x000101
[    0.192474] pci 0000:00:1f.2: reg 10: [io  0xec00-0xec07]
[    0.192488] pci 0000:00:1f.2: reg 14: [io  0xe800-0xe803]
[    0.192503] pci 0000:00:1f.2: reg 18: [io  0xe400-0xe407]
[    0.192517] pci 0000:00:1f.2: reg 1c: [io  0xe000-0xe003]
[    0.192532] pci 0000:00:1f.2: reg 20: [io  0xdc00-0xdc0f]
[    0.192580] pci 0000:00:1f.3: [8086:24d3] type 0 class 0x000c05
[    0.192639] pci 0000:00:1f.3: reg 20: [io  0xc800-0xc81f]
[    0.192717] pci 0000:01:00.0: [10de:0221] type 0 class 0x000300
[    0.192741] pci 0000:01:00.0: reg 10: [mem 0xfb000000-0xfbffffff]
[    0.192756] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff pref]
[    0.192770] pci 0000:01:00.0: reg 18: [mem 0xfa000000-0xfaffffff]
[    0.192807] pci 0000:01:00.0: reg 30: [mem 0xfc8e0000-0xfc8fffff pref]
[    0.192898] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.192909] pci 0000:00:01.0:   bridge window [mem 0xf8800000-0xfc8fffff]
[    0.192918] pci 0000:00:01.0:   bridge window [mem 0xd0700000-0xf06fffff pref]
[    0.192952] pci 0000:02:01.0: [8086:1019] type 0 class 0x000200
[    0.192975] pci 0000:02:01.0: reg 10: [mem 0xfc9e0000-0xfc9fffff]
[    0.192998] pci 0000:02:01.0: reg 18: [io  0x9c00-0x9c1f]
[    0.193066] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
[    0.193074] pci 0000:02:01.0: PME# disabled
[    0.193125] pci 0000:00:03.0: PCI bridge to [bus 02-02]
[    0.193133] pci 0000:00:03.0:   bridge window [io  0x9000-0x9fff]
[    0.193141] pci 0000:00:03.0:   bridge window [mem 0xfc900000-0xfc9fffff]
[    0.193180] pci 0000:03:01.0: [1412:1724] type 0 class 0x000401
[    0.193205] pci 0000:03:01.0: reg 10: [io  0xbc00-0xbc1f]
[    0.193220] pci 0000:03:01.0: reg 14: [io  0xb800-0xb87f]
[    0.193303] pci 0000:03:01.0: supports D2
[    0.193336] pci 0000:03:06.0: [1002:4752] type 0 class 0x000300
[    0.193363] pci 0000:03:06.0: reg 10: [mem 0xff000000-0xffffffff]
[    0.193380] pci 0000:03:06.0: reg 14: [io  0xffffff00-0xffffffff]
[    0.193397] pci 0000:03:06.0: reg 18: [mem 0xfffff000-0xffffffff]
[    0.193445] pci 0000:03:06.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.193488] pci 0000:03:06.0: supports D1 D2
[    0.193517] pci 0000:03:08.0: [8086:1050] type 0 class 0x000200
[    0.193541] pci 0000:03:08.0: reg 10: [mem 0xfeaff000-0xfeafffff]
[    0.193557] pci 0000:03:08.0: reg 14: [io  0xb400-0xb43f]
[    0.193637] pci 0000:03:08.0: supports D1 D2
[    0.193642] pci 0000:03:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.193650] pci 0000:03:08.0: PME# disabled
[    0.193696] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.193705] pci 0000:00:1e.0:   bridge window [io  0xa000-0xbfff]
[    0.193714] pci 0000:00:1e.0:   bridge window [mem 0xfca00000-0xfeafffff]
[    0.193723] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.193730] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.193753] pci_bus 0000:00: on NUMA node 0
[    0.193762] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.193888] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.193973] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.194040] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.194308]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.200422] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.200571] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.200726] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.200869] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.201010] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.201151] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.201303] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.201447] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.201760] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.201760] vgaarb: device added: PCI:0000:03:06.0,decodes=io+mem,owns=none,locks=none
[    0.201760] vgaarb: loaded
[    0.201760] vgaarb: bridge control possible 0000:03:06.0
[    0.201760] vgaarb: bridge control possible 0000:01:00.0
[    0.201760] i2c-core: driver [aat2870] using legacy suspend method
[    0.201760] i2c-core: driver [aat2870] using legacy resume method
[    0.201760] SCSI subsystem initialized
[    0.201762] libata version 3.00 loaded.
[    0.201762] usbcore: registered new interface driver usbfs
[    0.201762] usbcore: registered new interface driver hub
[    0.201762] usbcore: registered new device driver usb
[    0.201762] PCI: Using ACPI for IRQ routing
[    0.201762] PCI: pci_cache_line_size set to 64 bytes
[    0.201762] pci 0000:03:06.0: no compatible bridge window for [io  0xffffff00-0xffffffff]
[    0.201762] pci 0000:03:06.0: address space collision: [mem 0xfffff000-0xffffffff] conflicts with 0000:03:06.0 [mem 0xff000000-0xffffffff]
[    0.201762] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.201762] reserve RAM buffer: 000000003fe30000 - 000000003fffffff 
[    0.201762] reserve RAM buffer: 000000003ff30000 - 000000003fffffff 
[    0.201762] NetLabel: Initializing
[    0.201762] NetLabel:  domain hash size = 128
[    0.201762] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.201762] NetLabel:  unlabeled traffic allowed by default
[    0.201837] hpet clockevent registered
[    0.201844] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.201853] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.201864] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.208111] Switching to clocksource hpet
[    0.227927] AppArmor: AppArmor Filesystem Enabled
[    0.227977] pnp: PnP ACPI init
[    0.228058] ACPI: bus type pnp registered
[    0.228249] pnp 00:00: [bus 00-ff]
[    0.228256] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.228263] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.228269] pnp 00:00: [io  0x0d00-0xffff window]
[    0.228275] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.228280] pnp 00:00: [mem 0x00000000 window]
[    0.228286] pnp 00:00: [mem 0x40000000-0xffffffff window]
[    0.228396] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.228506] pnp 00:01: [dma 4]
[    0.228511] pnp 00:01: [io  0x0000-0x000f]
[    0.228517] pnp 00:01: [io  0x0081-0x0083]
[    0.228522] pnp 00:01: [io  0x0087]
[    0.228527] pnp 00:01: [io  0x0089-0x008b]
[    0.228535] pnp 00:01: [io  0x008f]
[    0.228540] pnp 00:01: [io  0x00c0-0x00df]
[    0.228614] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.228643] pnp 00:02: [io  0x0070-0x0071]
[    0.228660] pnp 00:02: [irq 8]
[    0.228744] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.229291] pnp 00:03: [io  0x0061]
[    0.229371] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.229395] pnp 00:04: [io  0x00f0-0x00ff]
[    0.229406] pnp 00:04: [irq 13]
[    0.229485] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.229641] pnp 00:05: [io  0x03f0-0x03f1]
[    0.229649] pnp 00:05: [io  0x03f2-0x03f3]
[    0.229654] pnp 00:05: [io  0x03f4-0x03f5]
[    0.229659] pnp 00:05: [io  0x03f7]
[    0.229668] pnp 00:05: [irq 6]
[    0.229673] pnp 00:05: [dma 2]
[    0.229806] pnp 00:05: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.230176] pnp 00:06: [io  0x03f8-0x03ff]
[    0.230188] pnp 00:06: [irq 4]
[    0.230364] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.230973] pnp 00:07: [io  0x02f8-0x02ff]
[    0.230985] pnp 00:07: [irq 3]
[    0.231160] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.231627] pnp 00:08: [io  0x0378-0x037f]
[    0.231639] pnp 00:08: [irq 7]
[    0.231785] pnp 00:08: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.231911] pnp 00:09: [io  0x0010-0x001f]
[    0.231918] pnp 00:09: [io  0x0022-0x003f]
[    0.231924] pnp 00:09: [io  0x0044-0x005f]
[    0.231929] pnp 00:09: [io  0x0062-0x0063]
[    0.231934] pnp 00:09: [io  0x0065-0x006f]
[    0.231939] pnp 00:09: [io  0x0072-0x007f]
[    0.231944] pnp 00:09: [io  0x0080]
[    0.231949] pnp 00:09: [io  0x0084-0x0086]
[    0.231954] pnp 00:09: [io  0x0088]
[    0.231959] pnp 00:09: [io  0x008c-0x008e]
[    0.231965] pnp 00:09: [io  0x0090-0x009f]
[    0.231976] pnp 00:09: [io  0x00a2-0x00bf]
[    0.231983] pnp 00:09: [io  0x00e0-0x00ef]
[    0.231988] pnp 00:09: [io  0x04d0-0x04d1]
[    0.232082] pnp 00:09: disabling [io  0x0010-0x001f] because it overlaps 0000:03:06.0 BAR 1 [io  0x0000-0x00ff]
[    0.232091] pnp 00:09: disabling [io  0x0022-0x003f] because it overlaps 0000:03:06.0 BAR 1 [io  0x0000-0x00ff]
[    0.232099] pnp 00:09: disabling [io  0x0044-0x005f] because it overlaps 0000:03:06.0 BAR 1 [io  0x0000-0x00ff]
[    0.232107] pnp 00:09: disabling [io  0x0062-0x0063] because it overlaps 0000:03:06.0 BAR 1 [io  0x0000-0x00ff]
[    0.232115] pnp 00:09: disabling [io  0x0065-0x006f] because it overlaps 0000:03:06.0 BAR 1 [io  0x0000-0x00ff]
[    0.232122] pnp 00:09: disabling [io  0x0072-0x007f] because it overlaps 0000:03:06.0 BAR 1 [io  0x0000-0x00ff]
[    0.232130] pnp 00:09: disabling [io  0x0080] because it overlaps 0000:03:06.0 BAR 1 [io  0x0000-0x00ff]
[    0.232137] pnp 00:09: disabling [io  0x0084-0x0086] because it overlaps 0000:03:06.0 BAR 1 [io  0x0000-0x00ff]
[    0.232145] pnp 00:09: disabling [io  0x0088] because it overlaps 0000:03:06.0 BAR 1 [io  0x0000-0x00ff]
[    0.232152] pnp 00:09: disabling [io  0x008c-0x008e] because it overlaps 0000:03:06.0 BAR 1 [io  0x0000-0x00ff]
[    0.232160] pnp 00:09: disabling [io  0x0090-0x009f] because it overlaps 0000:03:06.0 BAR 1 [io  0x0000-0x00ff]
[    0.232168] pnp 00:09: disabling [io  0x00a2-0x00bf] because it overlaps 0000:03:06.0 BAR 1 [io  0x0000-0x00ff]
[    0.232175] pnp 00:09: disabling [io  0x00e0-0x00ef] because it overlaps 0000:03:06.0 BAR 1 [io  0x0000-0x00ff]
[    0.232287] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.232296] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.232429] pnp 00:0a: [mem 0xffb00000-0xffbfffff]
[    0.232436] pnp 00:0a: [mem 0xfff00000-0xffffffff]
[    0.232534] pnp 00:0a: Plug and Play ACPI device, IDs INT0800 (active)
[    0.232903] pnp 00:0b: [io  0x0400-0x047f]
[    0.232911] pnp 00:0b: [io  0x0000-0xffffffff disabled]
[    0.232917] pnp 00:0b: [io  0x0680-0x06ff]
[    0.232922] pnp 00:0b: [io  0x0500-0x053f]
[    0.232927] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    0.232933] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
[    0.232938] pnp 00:0b: [mem 0xfed20000-0xfed9ffff]
[    0.233083] system 00:0b: [io  0x0400-0x047f] has been reserved
[    0.233091] system 00:0b: [io  0x0680-0x06ff] has been reserved
[    0.233098] system 00:0b: [io  0x0500-0x053f] has been reserved
[    0.233106] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.233113] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.233120] system 00:0b: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.233128] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.233604] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.233612] pnp 00:0c: [mem 0x000c0000-0x000dffff]
[    0.233617] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.233623] pnp 00:0c: [mem 0x00100000-0x3fffffff]
[    0.233628] pnp 00:0c: [mem 0x00000000-0xffffffff disabled]
[    0.233768] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.233776] system 00:0c: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.233783] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.233790] system 00:0c: [mem 0x00100000-0x3fffffff] could not be reserved
[    0.233798] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.234204] pnp: PnP ACPI: found 13 devices
[    0.234209] ACPI: ACPI bus type pnp unregistered
[    0.234217] PnPBIOS: Disabled by ACPI PNP
[    0.273455] pci 0000:03:06.0: address space collision: [mem 0xfffe0000-0xffffffff pref] conflicts with 0000:03:06.0 [mem 0xff000000-0xffffffff]
[    0.273468] PCI: max bus depth: 1 pci_try_num: 2
[    0.273497] pci 0000:00:1e.0: BAR 15: assigned [mem 0x40000000-0x400fffff pref]
[    0.273506] pci 0000:00:1f.1: BAR 5: assigned [mem 0x40100000-0x401003ff]
[    0.273518] pci 0000:00:1f.1: BAR 5: set to [mem 0x40100000-0x401003ff] (PCI address [0x40100000-0x401003ff])
[    0.273527] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.273536] pci 0000:00:01.0:   bridge window [mem 0xf8800000-0xfc8fffff]
[    0.273544] pci 0000:00:01.0:   bridge window [mem 0xd0700000-0xf06fffff pref]
[    0.273555] pci 0000:00:03.0: PCI bridge to [bus 02-02]
[    0.273562] pci 0000:00:03.0:   bridge window [io  0x9000-0x9fff]
[    0.273571] pci 0000:00:03.0:   bridge window [mem 0xfc900000-0xfc9fffff]
[    0.273587] pci 0000:03:06.0: BAR 6: assigned [mem 0x40000000-0x4001ffff pref]
[    0.273595] pci 0000:03:06.0: BAR 2: assigned [mem 0xfca00000-0xfca00fff]
[    0.273606] pci 0000:03:06.0: BAR 2: set to [mem 0xfca00000-0xfca00fff] (PCI address [0xfca00000-0xfca00fff])
[    0.273613] pci 0000:03:06.0: BAR 1: assigned [io  0xa000-0xa0ff]
[    0.273624] pci 0000:03:06.0: BAR 1: set to [io  0xa000-0xa0ff] (PCI address [0xa000-0xa0ff])
[    0.273630] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.273637] pci 0000:00:1e.0:   bridge window [io  0xa000-0xbfff]
[    0.273647] pci 0000:00:1e.0:   bridge window [mem 0xfca00000-0xfeafffff]
[    0.273656] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x400fffff pref]
[    0.273689] pci 0000:00:1e.0: setting latency timer to 64
[    0.273698] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.273704] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.273711] pci_bus 0000:01: resource 1 [mem 0xf8800000-0xfc8fffff]
[    0.273717] pci_bus 0000:01: resource 2 [mem 0xd0700000-0xf06fffff pref]
[    0.273724] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
[    0.273730] pci_bus 0000:02: resource 1 [mem 0xfc900000-0xfc9fffff]
[    0.273736] pci_bus 0000:03: resource 0 [io  0xa000-0xbfff]
[    0.273742] pci_bus 0000:03: resource 1 [mem 0xfca00000-0xfeafffff]
[    0.273748] pci_bus 0000:03: resource 2 [mem 0x40000000-0x400fffff pref]
[    0.273755] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.273761] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
[    0.273844] NET: Registered protocol family 2
[    0.273996] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.274492] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.275186] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.275588] TCP: Hash tables configured (established 131072 bind 65536)
[    0.275594] TCP reno registered
[    0.275602] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.275616] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.275783] NET: Registered protocol family 1
[    0.275853] pci 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.275878] pci 0000:00:1d.0: PCI INT A disabled
[    0.275905] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.275928] pci 0000:00:1d.1: PCI INT B disabled
[    0.275955] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.275976] pci 0000:00:1d.2: PCI INT C disabled
[    0.275992] pci 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.276061] pci 0000:00:1d.3: PCI INT A disabled
[    0.276087] pci 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.276124] pci 0000:00:1d.7: PCI INT D disabled
[    0.276165] pci 0000:01:00.0: Boot video device
[    0.276200] pci 0000:03:08.0: Firmware left e100 interrupts enabled; disabling
[    0.276212] PCI: CLS 64 bytes, default 64
[    0.276932] audit: initializing netlink socket (disabled)
[    0.276950] type=2000 audit(1009843247.272:1): initialized
[    0.315298] highmem bounce pool size: 64 pages
[    0.315310] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.320416] VFS: Disk quotas dquot_6.5.2
[    0.320565] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.321944] fuse init (API version 7.17)
[    0.322177] msgmni has been set to 1702
[    0.322941] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.322999] io scheduler noop registered
[    0.323004] io scheduler deadline registered
[    0.323020] io scheduler cfq registered (default)
[    0.323397] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.323448] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.323803] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.323817] ACPI: Sleep Button [SLPB]
[    0.323935] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.323944] ACPI: Power Button [PWRF]
[    0.327751] ERST: Table is not found!
[    0.327759] GHES: HEST is not enabled!
[    0.327980] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.336103] isapnp: Scanning for PnP cards...
[    0.348389] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.412340] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.690050] isapnp: No Plug & Play device found
[    0.739350] Freeing initrd memory: 13872k freed
[    0.804677] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.836432] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.848369] Linux agpgart interface v0.103
[    0.848639] agpgart-intel 0000:00:00.0: Intel i875 Chipset
[    0.851769] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf4000000
[    0.854608] brd: module loaded
[    0.856055] loop: module loaded
[    0.856298] ata_piix 0000:00:1f.1: version 2.13
[    0.856314] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.856324] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.856377] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.856954] scsi0 : ata_piix
[    0.857118] scsi1 : ata_piix
[    0.858553] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.858559] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.858608] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.858619] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.858684] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.859141] scsi2 : ata_piix
[    0.859282] scsi3 : ata_piix
[    0.860304] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 18
[    0.860310] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 18
[    0.861100] Fixed MDIO Bus: probed
[    0.861140] tun: Universal TUN/TAP device driver, 1.6
[    0.861144] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.861250] PPP generic driver version 2.4.2
[    0.861471] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.861499] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.861523] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.861530] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.861613] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.861650] ehci_hcd 0000:00:1d.7: debug port 1
[    0.865548] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.865573] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebffc00
[    0.880025] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.880279] hub 1-0:1.0: USB hub found
[    0.880287] hub 1-0:1.0: 8 ports detected
[    0.880429] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.880455] uhci_hcd: USB Universal Host Controller Interface driver
[    0.880486] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.880496] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.880501] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.880588] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.880629] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00
[    0.880862] hub 2-0:1.0: USB hub found
[    0.880870] hub 2-0:1.0: 2 ports detected
[    0.880980] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.880990] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.880995] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.881082] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.881120] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[    0.881359] hub 3-0:1.0: USB hub found
[    0.881366] hub 3-0:1.0: 2 ports detected
[    0.881472] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.881483] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.881488] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.881575] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.881602] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[    0.881823] hub 4-0:1.0: USB hub found
[    0.881831] hub 4-0:1.0: 2 ports detected
[    0.881939] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.881952] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.881957] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.882047] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.882073] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[    0.882301] hub 5-0:1.0: USB hub found
[    0.882309] hub 5-0:1.0: 2 ports detected
[    0.882502] usbcore: registered new interface driver libusual
[    0.882589] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.885781] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.885793] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.886038] mousedev: PS/2 mouse device common for all mice
[    0.886313] rtc_cmos 00:02: RTC can wake from S4
[    0.886455] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.886482] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.886606] device-mapper: uevent: version 1.0.3
[    0.886742] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.886781] EISA: Probing bus 0 at eisa.0
[    0.886821] EISA: Detected 0 cards.
[    0.886835] cpufreq-nforce2: No nForce2 chipset.
[    0.886839] cpuidle: using governor ladder
[    0.886842] cpuidle: using governor menu
[    0.886845] EFI Variables Facility v0.08 2004-May-17
[    0.887299] TCP cubic registered
[    0.887509] NET: Registered protocol family 10
[    0.888604] NET: Registered protocol family 17
[    0.888613] Registering the dns_resolver key type
[    0.888645] Using IPI No-Shortcut mode
[    0.888859] PM: Hibernation image not present or could not be loaded.
[    0.888881] registered taskstats version 1
[    0.901029]   Magic number: 2:0:0
[    0.901124] rtc_cmos 00:02: setting system clock to 2002-01-01 00:00:48 UTC (1009843248)
[    0.901153] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.901156] EDD information not available.
[    0.909665] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.037826] ata1.00: ATA-5: MAXTOR 6L060J3, A93.0500, max UDMA/133
[    1.037833] ata1.00: 117266688 sectors, multi 16: LBA 
[    1.037973] ata2.00: ATAPI: SAMSUNG CDRW/DVD SM-348B, T503, max UDMA/33
[    1.044372] ata2.00: configured for UDMA/33
[    1.052352] ata1.00: configured for UDMA/100
[    1.052550] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR 6L060J3   A93. PQ: 0 ANSI: 5
[    1.052786] sd 0:0:0:0: [sda] 117266688 512-byte logical blocks: (60.0 GB/55.9 GiB)
[    1.052873] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.052932] sd 0:0:0:0: [sda] Write Protect is off
[    1.052940] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.053002] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.053586] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SM-348B T503 PQ: 0 ANSI: 5
[    1.054686] sr0: scsi3-mmc drive: 1x/48x writer cd/rw xa/form2 cdda tray
[    1.054691] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.054889] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.055080] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.094124]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.094966] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.095007] Freeing unused kernel memory: 716k freed
[    1.095449] Write protecting the kernel text: 5636k
[    1.095529] Write protecting the kernel read-only data: 2332k
[    1.126904] udevd[94]: starting version 175
[    1.192138] usb 1-2: new high-speed USB device number 2 using ehci_hcd
[    1.276057] Refined TSC clocksource calibration: 2792.999 MHz.
[    1.276069] Switching to clocksource tsc
[    1.315519] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    1.315527] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    1.315589] e1000 0000:02:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.315603] e1000 0000:02:01.0: setting latency timer to 64
[    1.316053] Floppy drive(s): fd0 is 1.44M
[    1.334801] FDC 0 is a post-1991 82077
[    1.339482] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.339490] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.339570] e100 0000:03:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.364264] e100 0000:03:08.0: PME# disabled
[    1.369777] e100 0000:03:08.0: eth0: addr 0xfeaff000, irq 20, MAC addr 00:11:11:52:95:12
[    1.748686] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    1.754819] e1000 0000:02:01.0: eth1: (PCI:33MHz:32-bit) 00:11:11:52:95:09
[    1.754833] e1000 0000:02:01.0: eth1: Intel(R) PRO/1000 Network Connection
[    1.772050] usb 4-1: new low-speed USB device number 2 using uhci_hcd
[    2.196022] usb 4-2: new full-speed USB device number 3 using uhci_hcd
[   23.922173] Adding 1046524k swap on /dev/sda7.  Priority:-1 extents:1 across:1046524k 
[   23.932538] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.932555] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   24.029789] udevd[313]: starting version 175
[   24.255266] lp: driver loaded but no devices found
[   24.340181] Intel 82802 RNG detected
[   24.381239] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.488412] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   24.527739] i801_smbus 0000:00:1f.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   24.559188] parport_pc 00:08: reported by Plug and Play ACPI
[   24.559217] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   24.587328] udevd[362]: renamed network interface eth0 to rename2
[   24.601474] udevd[360]: renamed network interface eth1 to eth2
[   24.648426] lp0: using parport0 (interrupt-driven).
[   24.661820] udevd[362]: renamed network interface rename2 to eth1
[   24.937471] cfg80211: Calling CRDA to update world regulatory domain
[   25.049667] type=1400 audit(1009861272.646:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=570 comm="apparmor_parser"
[   25.049689] type=1400 audit(1009861272.646:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=559 comm="apparmor_parser"
[   25.051555] type=1400 audit(1009861272.646:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=570 comm="apparmor_parser"
[   25.051612] type=1400 audit(1009861272.646:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=559 comm="apparmor_parser"
[   25.052426] type=1400 audit(1009861272.650:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=559 comm="apparmor_parser"
[   25.055278] type=1400 audit(1009861272.650:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=570 comm="apparmor_parser"
[   25.056970] type=1400 audit(1009861272.654:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=552 comm="apparmor_parser"
[   25.058496] type=1400 audit(1009861272.654:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=552 comm="apparmor_parser"
[   25.059158] type=1400 audit(1009861272.654:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=552 comm="apparmor_parser"
[   25.099742] usbcore: registered new interface driver usbserial
[   25.099779] USB Serial support registered for generic
[   25.099872] usbcore: registered new interface driver usbserial_generic
[   25.099878] usbserial: USB Serial Driver core
[   25.128131] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input3
[   25.129294] ppdev: user-space parallel port driver
[   25.134560] generic-usb 0003:093A:2500.0001: input,hidraw0: USB HID v1.10 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.2-1/input0
[   25.134652] usbcore: registered new interface driver usbhid
[   25.134658] usbhid: USB HID core driver
[   25.338937] cfg80211: World regulatory domain updated:
[   25.338943] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.338949] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.338953] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.338957] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.338961] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.338965] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.365767] USB Serial support registered for DeLorme Earthmate USB
[   25.365808] USB Serial support registered for HID->COM RS232 Adapter
[   25.365843] USB Serial support registered for Nokia CA-42 V2 Adapter
[   25.365892] cypress 4-2:1.0: DeLorme Earthmate USB converter detected
[   25.372243] usb 4-2: DeLorme Earthmate USB converter now attached to ttyUSB0
[   25.372429] usbcore: registered new interface driver cypress
[   25.372436] cypress_m8: v1.10:Cypress USB to Serial Driver
[   25.445730] init: failsafe main process (666) killed by TERM signal
[   25.732055] usb 1-2: reset high-speed USB device number 2 using ehci_hcd
[   25.806939] Bluetooth: Core ver 2.16
[   25.807045] NET: Registered protocol family 31
[   25.807051] Bluetooth: HCI device and connection manager initialized
[   25.807058] Bluetooth: HCI socket layer initialized
[   25.807063] Bluetooth: L2CAP socket layer initialized
[   25.807076] Bluetooth: SCO socket layer initialized
[   25.838225] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.838233] Bluetooth: BNEP filters: protocol multicast
[   25.902677] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   25.902687] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.902693] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   25.902700] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.902706] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   25.902713] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.902719] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   25.902725] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.902731] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   25.902738] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.902744] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   25.902751] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.902757] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   25.902764] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.902770] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   25.902777] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.902783] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   25.902790] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.902796] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   25.902803] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.902809] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   25.902816] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.902822] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   25.902829] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.902835] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   25.902842] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.902848] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   25.902855] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.113926] type=1400 audit(1009861273.710:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=759 comm="apparmor_parser"
[   26.171932] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   26.173970] Registered led device: rt2800usb-phy0::radio
[   26.174038] Registered led device: rt2800usb-phy0::assoc
[   26.174100] Registered led device: rt2800usb-phy0::quality
[   26.174167] usbcore: registered new interface driver rt2800usb
[   26.196271] Bluetooth: RFCOMM TTY layer initialized
[   26.196284] Bluetooth: RFCOMM socket layer initialized
[   26.196290] Bluetooth: RFCOMM ver 1.11
[   26.818342] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   26.819056] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   27.021033] nvidia: module license 'NVIDIA' taints kernel.
[   27.021038] Disabling lock debugging due to kernel taint
[   27.076510] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.218495] snd_ice1724 0000:03:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   27.253762] ice1724: No matching model found for ID 0xc3140517
[   27.256632] ice1724: Invalid EEPROM version 1
```

---

### Post by Elfy on 2013-10-14
Threads merged

---

### Post by varunendra on 2013-10-14
> **sdowney717 said:**
> 
```

Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...[COLOR="#FF0000"]Failed[/COLOR].

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
....
....
**Tue Jan  1 00:04:32 EST 2002: Running hooks for resume**
....
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager [COLOR="#FF0000"]wake interfaces back up...Failed[/COLOR].

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
```
Please try this, just as a test -

* Disable Network Manager

* Go into BIOS > disable all network interfaces > save & exit.

* If you are using a USB wifi adapter, don't plug it in, so that no driver is loaded for it.

* Boot into Ubuntu and make sure no network drivers are loaded -
```
lsmod | egrep 'rt2|e100'
```
..there should be no output

* Now suspend > wait for at least 30 seconds > resume.

Any improvement?

---

### Post by sdowney717 on 2013-10-14
Ok, next time I get there I can try this but it will be on tuesday.

I did try removing the usb wireless and it still would not awaken.
The other network are 2 builtin motherboard ethernet ports.

This is an intel serverboard pentium 4 processor 2.8ghz. I have an Nvidia AGP video card and it is running Nvidia driver.

[http://www.geeks.com/details.asp?invtid=S875WP1-E-P428-NP](http://www.geeks.com/details.asp?invtid=S875WP1-E-P428-NP)

It dualboots with XP and when booted XP it awakens properly after a suspend.

---

### Post by varunendra on 2013-10-14
> **sdowney717 said:**
> I did try removing the usb wireless and it still would not awaken.
Once the driver for the USB adapter is loaded, it remains loaded even if you remove the adapter. It is usually buggy drivers/firmware/related power management that causes it to fail to unload during suspend. So if the module doesn't load at all, these possibilities are eliminated.

> The other network are 2 builtin motherboard ethernet ports.
Yeah, figured that looking at the drivers (e100, e1000). :)
They usually work in 'bridged' mode, sometimes that may cause issues too.

Our target is to rule out the possibility of any of the network drivers or the interface or the Network Manager itself being the culprit. If they are, the suspend-resume will work with these removed/disabled. If it still fails, then we need to dig deeper.

---

### Post by sdowney717 on 2013-10-16
I removed the hard-drive and booted an identical system using that same drive and the desktop suspended and awoke perfectly. Exact same MB and ram.

The other system I found the CMOS battery has failed but win7 was able to resume ok so dont know if a cmos battery would be the problem.
The one that wont awaken runs nvidia driver. The one that does awaken has an AMD video card but running the free driver.

What I will do is swap video cards when I get out there and update the thread.

Could the nvidia driver be the problem?

---

### Post by varunendra on 2013-10-17
> **sdowney717 said:**
> Could the nvidia driver be the problem?

Could be (from [https://wiki.archlinux.org/index.php/Pm-utils#Standby.2Fsuspend_to_RAM](https://wiki.archlinux.org/index.php/Pm-utils#Standby.2Fsuspend_to_RAM)) -
> In some cases, it is possible that running pm-suspend causes hangs or other issues. This may be due to specific "misbehaving" modules. If you know which modules could cause such issues, adding a SUSPEND_MODULES config to /etc/pm/config.d/modules of the form:
```
SUSPEND_MODULES="uhci_hd button ehci_hd iwlwifi"
```
should cause these modules to be specifically unloaded before suspend and reloaded after resume.

..but is better to test than guess. If it's fixed, maybe adding the nvidia driver to /etc/pm/config.d/modules file should help. If not, there are some options we can try with Grub boot parameters.

---

### Post by sdowney717 on 2013-10-18
Really weird things happening now.
I have 2 of these MBoards.
One at the house and one at the boat.
house has AMD card.
boat has Nvidia card.
otherwise same MB and identical ram.

Now the one here at the house with AMD card, was suspending and awakening ok and that with the hard drive from the boat's PC.
So I goto boat and retrieve the Nvidia card. Put it into house PC and now it suspends and immediately awakens and does a reboot with bios screen flash, and then keyboard will not respond? Have to unplug power and reboot to get keyboard back.

So I put the AMD card back into house PC and it suspends and immediately awakens and does a reboot and the keyboard responds?

So now every time the house PC suspends, it awakens after about a second after shutting down and does a reboot with bios screen flash. And all I did was swap video cards?
Suspend now broken on both MB.
???

So suspend is now rebooting the PC.

---

### Post by sdowney717 on 2013-10-18
ok, just ignore the prior post. I turned it off, unplugged all the cords and let it sit timeout for awhile.
Now it is back to working like it used to. 

It is definitely the Nvidia card.
It will suspend and awaken ok with the AMD card.
The Nvidia card it will not awaken, verified.

---

### Post by sdowney717 on 2013-10-18
ok i created that file and this is what is in there now.
cmd to open that file
sudo gedit /etc/pm/config.d/modules

is the nvidia correct?

```
SUSPEND_MODULES="uhci_hd button ehci_hd iwlwifi nvidia"
```

I tried this and it still will not awaken

---

### Post by sdowney717 on 2013-10-18
I discovered it is definitely the Nvidia driver 304.88
This is an older 6200 AGP card.
If it runs the free driver, then it awakes properly from suspend.

NOW, is it worth trying an upgrade from 12.04 LTS to 13.10 to see if the nvidia driver can suspend and awake properly???

OR, is there an older driver to try that might work properly???

OR, does anyone have thoughts on how to make it work as is?

---

### Post by varunendra on 2013-10-18
> **sdowney717 said:**
> is the nvidia correct?

```
SUSPEND_MODULES="[COLOR="#FF0000"]uhci_hd button ehci_hd iwlwifi[/COLOR] nvidia"
```

The other entries highlighted in red were only for example and not needed. Moreover, I think there is no such driver as uhci_hd or ehci_hd in Ubuntu. They are ..**h[COLOR="#FF0000"]c[/COLOR]d**, not **hd** here. But anyway, that is not related now that you have verified that it is specifically related to the graphics card.

The "**nvidia**" entry above is correct **IF** it is the module name that is loading for your card. The native drivers are nouveau and nvidiafb, not sure about the names of the proprietary variants. You can check it with -
```
lspci -nnk | grep -iA2 vga
```
..and look at the last line "Kernel driver in use:". Which one is in use? The same name should be used in above file.

> **sdowney717 said:**
> NOW, is it worth trying an upgrade from 12.04 LTS to 13.10 to see if the nvidia driver can suspend and awake properly???
I think you can check it in the live session too to make sure it works, before deciding to install/upgrade to it. But first make sure you are using correct driver name in the "modules" file above.

There are some boot parameters as well that you may try, especially those related to acpi : [https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)
You can try them temporarily during boot time, or apply them permanently as mentioned in this thread : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) (the above wiki page also mentions using "Boot-Repair" which makes applying these changes a lot safer and easier).

I am not very familiar with graphics related issues, but can we see modinfo of the driver you are using? For example, if it is indeed "nvidia" then -
```
modinfo [COLOR="#FF0000"]nvidia[/COLOR]
```
..and also -
```
sudo grep -R [[:graph:]] /sys/module/[COLOR="#FF0000"]nvidia[/COLOR]/parameters
```
..to let us see what parameters the driver is currently loading with. Of course replace "nvidia" with the driver actually in use by your card.

---

### Post by sdowney717 on 2013-10-18
```
scott@scott-P5QC:~$ sudo grep -R [[:graph:]] /sys/module/nvidia/parameters
[sudo] password for scott: 
grep: /sys/module/nvidia/parameters: No such file or directory
scott@scott-P5QC:~$ modinfo nvidia
ERROR: modinfo: could not find module nvidia
scott@scott-P5QC:~$ 

```

Thanks for the help so far. I see it is not nvidia.
How do you know the name that it is using?

---

### Post by sdowney717 on 2013-10-18
It may be called nvidia-304

```
scotts875@scotts875-desktop:~$ modinfo nvidia-304
filename:       /lib/modules/3.8.0-19-generic/updates/dkms/nvidia_304.ko
alias:          char-major-195-*
version:        304.88
supported:      external
license:        NVIDIA
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd00000AA3sv*sd*bc0Bsc40i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        
vermagic:       3.8.0-19-generic SMP mod_unload modversions 686 
parm:           NVreg_EnableVia4x:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UseVBios:int
parm:           NVreg_RMEdgeIntrCheck:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_NvAGP:int


```


```
scotts875@scotts875-desktop:~$ sudo grep -R [[:graph:]] /sys/module/nvidia-304/parameters
grep: /sys/module/nvidia-304/parameters: No such file or directory
scotts875@scotts875-desktop:~$ 
```

I also edited the file  /etc/pm/config.d/modules from nvidia to nvidia-304 and it did not help.

---

### Post by varunendra on 2013-10-18
The kernel module name (the actual file in the kernel tree) can be sometimes different than what it is called by. Did you check it this way as I mentioned ? -
> You can check it with -
```
lspci -nnk | grep -iA2 vga
```
..and look at the last line "Kernel driver in use:". Which one is in use? The same name should be used in above file.
I'd suggest you post the whole output of above as it will also tell us exactly what chip it is using (although I can't offer much help on that, but maybe others can :)).

And let us see what it is listed as in lsmod -
```
lsmod
```
Also note that not all modules create a "parameters" directory in /sys/module/<driver name>". We'll check it after confirming the module name.

---

### Post by sdowney717 on 2013-10-19
```
scotts875@scotts875-desktop:~$ lsmod
Module                  Size  Used by
nvidia              10287297  40 
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202069  10 bnep,rfcomm
binfmt_misc            17260  1 
ppdev                  12817  0 
snd_emu10k1_synth      13007  0 
snd_emux_synth         33483  1 snd_emu10k1_synth
snd_seq_midi_emul      13443  1 snd_emux_synth
snd_seq_virmidi        13220  1 snd_emux_synth
snd_emu10k1           136596  3 snd_emu10k1_synth
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  2 snd_emux_synth,snd_emu10k1
snd_ac97_codec        105692  1 snd_emu10k1
ac97_bus               12670  1 snd_ac97_codec
cypress_m8             18165  0 
usbserial              27423  1 cypress_m8
snd_pcm                80890  2 snd_ac97_codec,snd_emu10k1
microcode              18286  0 
snd_page_alloc         14230  2 snd_pcm,snd_emu10k1
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25114  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq                51280  5 snd_seq_midi_event,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi
parport_pc             27504  1 
snd_seq_device         14137  5 snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi
snd_timer              24411  3 snd_pcm,snd_seq,snd_emu10k1
emu10k1_gp             12541  0 
snd                    56485  14 snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_device
soundcore              12600  1 snd
gameport               15016  2 emu10k1_gp
mac_hid                13037  0 
lpc_ich                16925  0 
intel_rng              12700  0 
shpchp                 32129  0 
serio_raw              13031  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
e100                   35903  0 
e1000                 104054  0 
floppy                 55441  0 

```

```

scotts875@scotts875-desktop:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV44A [GeForce 6200] [10de:0221] (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:0130]
	Kernel driver in use: nvidia
--
03:06.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Rage XL PCI [1002:4752] (rev 27)
	Subsystem: Intel Corporation Device [8086:3428]
03:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 01)
scotts875@scotts875-desktop:~$ 
```

looks like it is called nvidia

---

### Post by varunendra on 2013-10-19
> **sdowney717 said:**
> 
```

scotts875@scotts875-desktop:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV44A [GeForce 6200] [10de:0221] (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:0130]
	Kernel driver in use: **[COLOR="#FF0000"]nvidia[/COLOR]**
--
03:06.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Rage XL PCI [1002:4752] (rev 27)
	Subsystem: Intel Corporation Device [8086:3428]
03:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 01)
scotts875@scotts875-desktop:~$ 
```

looks like it is called nvidia

Indeed. It is probably the same driver that you checked initially - "nvidia-304.ko". Does its modinfo confirm that? -
```
modinfo nvidia
```

And what is that ATI card below it? An extra card or something onboard. Either way, doesn't seem to have any drivers attached, which in my experience is unusual.

---

### Post by sdowney717 on 2013-10-19
These MB's have built in onboard video. That is what that is.

---

### Post by sdowney717 on 2013-10-19
modinfo only yields data as nvidia-304
304.88 is the nvidia driver version


[B]```
scotts875@scotts875-desktop:~$ modinfo nvidia
ERROR: Module nvidia not found.
[/B]

scotts875@scotts875-desktop:~$ modinfo nvidia-304
filename:       /lib/modules/3.8.0-19-generic/updates/dkms/nvidia_304.ko
alias:          char-major-195-*
version:        304.88
supported:      external
license:        NVIDIA
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd00000AA3sv*sd*bc0Bsc40i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        
vermagic:       3.8.0-19-generic SMP mod_unload modversions 686 
parm:           NVreg_EnableVia4x:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UseVBios:int
parm:           NVreg_RMEdgeIntrCheck:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_NvAGP:int
scotts875@scotts875-desktop:~$ 

```

---

