---
title: "m1330: Suspend issues since 9.04 update"
date: 2009-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pormogo on 2009-05-05
So after I got to enabling UXA support for my video chipset after updating to 9.04 I'm close to thinking this is about the best release of Ubuntu to date. However I have run into some issues with the suspend function since updating to 9.04. 

It seems like if I suspend the machine more then once when it's up it doesn't suspend correctly. For example if I suspend the machine on my way to work and then wake it up at work it's just fine. When I go home I suspend it again, however upon waking it up when I get home I seem to have totally lost my gnome session. That second suspend always seems to loose my session. 

I have to log back in via GDM and everything that I was working on is gone :confused:

Has anyone else run into an issue like this? I've been googling around but I haven't really seen anyone post or complain about any issues like this. Is there something that I'm missing?

There appear to be bugs posted but there isn't a lot of movement in those threads. I'm planning on contributing my info to the bugs later on today

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/334756](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/334756)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/358966](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/358966)

---

### Post by pormogo on 2009-05-18
Well I'm still having this issue. I was thinking/hoping that standard package updates would catch whatever is causing this issue to happen but that doesn't seem to be the case. I'm a little lost as to where to turn next. Here's my /var/log/pm-suspend.log file. 

```

Initial commandline parameters: --quirk-vbemode-restore
--quirk-vbe-post
**Mon May 18 10:23:10 PDT 2009: Running hooks for suspend.**
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux Fenrir 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
i915                   65540  2
drm                    96296  3 i915
binfmt_misc            16776  1
ppdev                  15620  0
bridge                 56340  0
stp                    10500  1 bridge
bnep                   20224  2
input_polldev          11912  0
coretemp               13952  0
sbp2                   30476  0
lp                     17156  0
parport                42220  2 ppdev,lp
joydev                 18368  0
snd_hda_intel         435636  5
snd_pcm_oss            46336  0
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
arc4                    9856  2
ecb                    10752  2
snd_seq_dummy          10756  0
snd_seq_oss            37760  0
snd_seq_midi           14336  0
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwl3945                97912  0
uvcvideo               63240  0
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217208  1 iwl3945
psmouse                61972  0
intel_agp              34108  1
iTCO_wdt               19108  0
sdhci_pci              15232  0
sdhci                  23940  1 sdhci_pci
ricoh_mmc              11904  0
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
video                  25360  0
led_class              12036  1 iwl3945
snd                    62628  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                 15264  0
agpgart                42696  3 drm,intel_agp
serio_raw              13316  0
pcspkr                 10496  0
iTCO_vendor_support    11652  1 iTCO_wdt
soundcore              15200  1 snd
output                 11008  1 video
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
cfg80211               38032  2 iwl3945,mac80211
ohci1394               38576  0
ieee1394               94660  2 sbp2,ohci1394
tg3                   131204  0
fbcon                  46112  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
             total       used       free     shared    buffers     cached
Mem:       3605100    1799324    1805776          0     178136    1099560
-/+ buffers/cache:     521628    3083472
Swap:      3004112          0    3004112
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: sudo: no passwd entry for 1000!
success.
/usr/lib/pm-utils/sleep.d/45iwlist suspend suspend: sudo: no passwd entry for 1000!
/sbin/iwlist
not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90chvt suspend suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/etc/pm/sleep.d/99laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
[b]Mon May 18 10:23:13 PDT 2009: performing suspend
Mon May 18 10:51:32 PDT 2009: Awake.
Mon May 18 10:51:32 PDT 2009: Running hooks for resume[/b]
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
/etc/pm/sleep.d/99laptop-mode resume suspend: Laptop mode disabled, not active
success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: /usr/lib/pm-utils/sleep.d/95hdparm-apm: 50: get_power_status: not found

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
success.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90chvt resume suspend: success.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci resume suspend: No devices in HID mode found
Returned exit code 1.
/usr/lib/pm-utils/sleep.d/45iwlist resume suspend: /sbin/iwlist
eth1      Scan completed :
          Cell 01 - Address: 00:1B:2F:E2:01:E4
                    ESSID:"quarry"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/100  Signal level:-69 dBm  Noise level=-99 dBm
                    Encryption key:on
                    IE: Unknown: 0006717561727279
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD840050F204104A00011010440001011041000100103B000103104700103C63D30D6F4A85B4360BAF320D4BFD4F102100074E4554474541521023000857475236313476381024000857475236313476381042000538333235381054000800060050F20400011011001657475236313476382028576972656C65737320415029100800020084
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000031f81e21183
                    Extra: Last beacon: 1280ms ago
          Cell 02 - Address: 00:1E:2A:50:BD:B2
                    ESSID:"ArchionN"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/100  Signal level:-84 dBm  Noise level=-99 dBm
                    Encryption key:on
                    IE: Unknown: 000841726368696F6E4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201F0010000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000016b17c63b20
                    Extra: Last beacon: 1372ms ago
          Cell 03 - Address: 00:13:10:9D:41:3B
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/100  Signal level:-79 dBm  Noise level=-99 dBm
                    Encryption key:on
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020105
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000007a6a64b769
                    Extra: Last beacon: 1200ms ago
          Cell 04 - Address: 00:18:F8:A8:85:21
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/100  Signal level:-85 dBm  Noise level=-99 dBm
                    Encryption key:off
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000000a631e3d4
                    Extra: Last beacon: 1196ms ago

success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.

```

I bolded the suspend/resume times so it's easier to see the sequence itself. I can't see anything failing, and I guess that is technically correct. The system does suspend and come back from suspend, it's just logged me out and leaves me staring at a new gdm screen ](*,)

---

### Post by coffeeaddict22 on 2009-05-21
Haven't got a definite answer, but a couple of suggestions.  
First, try upgrading the BIOS.  Have a look [here]("http://linux.dell.com/projects.shtml")
Second, there's a forum thread about the DSDT which seems to address the same sort of problem.  Have a look [here]("http://www.uluga.ubuntuforums.org/showthread.php?t=1036051") for some more info.

---

### Post by pormogo on 2009-05-27
Well I updated my BIOS from A8 to A15 a few minutes ago. Hopefully this will fx my issue. I'll let you know when I get home tonight and bring this thing out of suspension. I'm in no way excited to mess with the DSDT so I hope this clears up my issue.

I can't imagine it's a DSDT issue. This latop, the m1330n is sold with ubuntu preinstalled I would be super surprised if for some reason the DSDT was compiled incorrectly for linux (especially since in my understanding that doesn't change without a bios flash the DSDT that is).

EDIT: HA! I found this in a gdm log file and I'm thinking it might be the culperate!

from /var/log/gmd/:0.log
*error setting MTRR (base = 0xe0000000, size = 0x10000000, type = 1) Invalid argument (22)*

---

