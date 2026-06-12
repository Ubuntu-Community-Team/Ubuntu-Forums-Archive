---
title: "Spontaneous wake up from suspend"
date: 2009-05-21
forum: General Help
---

### Post by Cl0ud9 on 2009-05-21
Since upgrading to 9.04, I am experiencing an odd problem with suspend. Whenever I close the lid to my laptop, suspend works correctly, but spontaneously wakes up on its own. I will close the lid to my laptop and see that it did suspend correctly, but after leaving the laptop sit for a few hours, I come back and see that it has waken up and is very warm. I didn't have this problem with 8.10.

Here is the output of cat /var/log/pm-suspend.log

```

Initial commandline parameters: --quirk-vbestate-restore
--quirk-vbe-post
Thu May 21 20:34:55 EDT 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux jesse-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
michael_mic            10496  4 
arc4                    9856  4 
ecb                    10752  4 
ieee80211_crypt_tkip    16896  2 
aes_i586               15744  1 
aes_generic            35880  1 aes_i586
ieee80211_crypt_ccmp    13440  1 
radeon                342816  2 
drm                    96296  3 radeon
vboxdrv                79936  0 
input_polldev          11912  0 
lp                     17156  0 
joydev                 18368  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
pcmcia                 44748  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
ipw2200               150984  0 
intel_agp              34108  0 
psmouse                61972  0 
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
agpgart                42696  2 drm,intel_agp
ppdev                  15620  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
dcdbas                 15264  0 
ieee80211              38344  1 ipw2200
ieee80211_crypt        13444  3 ieee80211_crypt_tkip,ieee80211_crypt_ccmp,ieee80211
serio_raw              13316  0 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
pcspkr                 10496  0 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
video                  25360  0 
output                 11008  1 video
tg3                   131204  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
             total       used       free     shared    buffers     cached
Mem:       1026492     906556     119936          0     439220     246180
-/+ buffers/cache:     221156     805336
Swap:      2000084        232    1999852
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/usr/lib/pm-utils/sleep.d/45iwlist suspend suspend: /sbin/iwlist
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
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: not applicable.
/etc/pm/sleep.d/99laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
Allocated buffer at 0x2010 (base is 0x0)
ES: 0x0201 EBX: 0x0000
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Thu May 21 20:34:56 EDT 2009: performing suspend
Thu May 21 20:35:14 EDT 2009: Awake.
Thu May 21 20:35:14 EDT 2009: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: Function not supported
success.
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
          Cell 01 - Address: 00:0F:66:D2:B6:A6
                    ESSID:"sysin"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=73/100  Signal level=-55 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 240ms ago
          Cell 02 - Address: 00:12:0E:85:4D:D1
                    ESSID:"verizon"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=27/100  Signal level=-83 dBm  
                    Extra: Last beacon: 1876ms ago
          Cell 03 - Address: 00:12:0E:85:B4:E0
                    ESSID:"07FX08069442"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-79 dBm  
                    Extra: Last beacon: 244ms ago

success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.

```

---

