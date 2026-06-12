---
title: "X session resets after suspend with Compiz enabled"
date: 2009-04-28
forum: Desktop Environments
---

### Post by kennymchansen on 2009-04-28
Compiz is working perfectly, and acpi functionality is working. The only problem is that when i try to resume after suspend i have been logged out of the X session i were currently working on. I am presentet with the log on screen and all open windows have been closed. This only happens when visual effects are enabled... 

I guess i dont need the effects, but i just think it is weird that I have to choose between suspend or Compiz... 

I am running Jaunty on a Lenovo 3000 v200 vith intel 965 express graphics. 

If it helps, here is the output of my pm-suspend.log:
```

Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Tue Apr 28 19:43:03 CEST 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux kh-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
hidp                   22272  0 
aes_i586               15744  1 
aes_generic            35880  1 aes_i586
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
sbp2                   30476  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
iwlagn                100228  0 
iwlcore                93184  1 iwlagn
snd_hda_intel         435636  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
led_class              12036  1 iwlcore
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217208  2 iwlagn,iwlcore
gspca_m5602            51212  0 
snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
gspca_main             30464  1 gspca_m5602
soundcore              15200  1 snd
sdhci_pci              15232  0 
psmouse                61972  0 
videodev               44960  1 gspca_main
cfg80211               38032  3 iwlagn,iwlcore,mac80211
sdhci                  23940  1 sdhci_pci
pcspkr                 10496  0 
serio_raw              13316  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
v4l1_compat            21764  1 videodev
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
btusb                  19608  2 
video                  25360  0 
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  2 sbp2,ohci1394
tg3                   131204  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
             total       used       free     shared    buffers     cached
Mem:       3087860    1994668    1093192          0     769068     900736
-/+ buffers/cache:     324864    2762996
Swap:       931728          0     931728
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
Tue Apr 28 19:43:05 CEST 2009: performing suspend
Tue Apr 28 19:43:15 CEST 2009: Awake.
Tue Apr 28 19:43:15 CEST 2009: Running hooks for resume
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
```

---

### Post by dro0g on 2009-04-29
I'm seeing this as well on a Dell D630 with an Intel 965. It only started happening recently. 

On the plus side, since X restarts when it comes back from suspend, it detects if monitors have changed and I'm not left blindly typing in my password and then trying to run xrandr --auto :)

---

### Post by JamesHowlett on 2009-04-30
Just like to add that I'm having this problem as well AND had it in Intrepid (8.10).  My chipset is intel 945GM though, and my pm-suspend.log looks pretty much the same as OP.

---

