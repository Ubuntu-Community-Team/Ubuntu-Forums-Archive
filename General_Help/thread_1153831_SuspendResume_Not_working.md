---
title: "Suspend/Resume Not working"
date: 2009-05-09
forum: General Help
---

### Post by yma981 on 2009-05-09
Hello 

I am used to suspending/resuming my pc for easy access. unfortunately under ubuntu 9.04 it is not working. I am forced to power off the system in order to reboot.

I tried ./quirk-checker.sh (Ubuntu help)
[http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-debug.html](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-debug.html)

That is the result: 

:~$ ./quirk-checker.sh
-e Checking your system...

WARNING: iwl3945 is usually okay for suspend - but it might be worth trying unloading it.

Suggestions:

-e Add 'SUSPEND_MODULES="iwl3945"' to /etc/pm/config.d/unload_modules!

********************

1- I can't find unload_modules in the specified folder
2- I can find 00sleep_module
3- it is not editable (permission issue)

Any Help please ??? 

Thanks
YMA

---

### Post by nealklomp on 2009-05-09
Bumb and ditto. Suspend not working.

---

### Post by yma981 on 2009-05-11
Any Help Pleaseeeeeeeeeeeeeeeeee?????

Thanks

---

### Post by yma981 on 2009-05-11
Please Suspend is essential for me and i am a new convert to ubuntu from windows .... Any help lovely community....

I read in another post that maybe acpi is off 


This is the content of /var/log/pm-suspend.log        


Initial commandline parameters: --quirk-vbestate-restore
Sat May  9 03:16:09 EEST 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux YMA 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
arc4                    9856  2 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
ecb                    10752  2 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
intel_agp              34108  1 
iwl3945                97912  0 
iTCO_wdt               19108  0 
ricoh_mmc              11904  0 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217208  1 iwl3945
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
iTCO_vendor_support    11652  1 iTCO_wdt
agpgart                42696  3 drm,intel_agp
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
input_polldev          11912  0 
psmouse                61972  0 
serio_raw              13316  0 
led_class              12036  1 iwl3945
cfg80211               38032  2 iwl3945,mac80211
pcspkr                 10496  0 
video                  25360  0 
output                 11008  1 video
uvcvideo               63240  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
             total       used       free     shared    buffers     cached
Mem:       3087376     829780    2257596          0      48752     425232
-/+ buffers/cache:     355796    2731580
Swap:      3004112          0    3004112
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
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/etc/pm/sleep.d/99laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Sat May  9 03:16:11 EEST 2009: performing suspend

---

