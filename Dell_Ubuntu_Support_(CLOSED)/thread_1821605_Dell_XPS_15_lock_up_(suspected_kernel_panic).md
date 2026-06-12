---
title: "Dell XPS 15 lock up (suspected kernel panic)"
date: 2011-08-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Fallen_Demon on 2011-08-09
Hi. I've got myself a brand new Dell XPS laptop and aside from the nVidia optimus stuff not working as intended (even bumblebee seems to do nothing), Ubuntu Natty runs pretty sweet. 

One problem I am having, though, is that I will get random lock ups from time to time after leaving the lappy idling for a little while. I will either come back and have it stuck on the screensaver (can't even switch to a tty to restart X), or it will work ok for a bit then just crash when I go to do something that I wasn't doing before. 

uname -a
> 
Linux freefall 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


Here's lsmod:
> 
Module                  Size  Used by
sha256_generic         21031  2 
cryptd                 20510  0 
aes_x86_64             17208  450 
aes_generic            38279  1 aes_x86_64
parport_pc             36959  0 
ppdev                  17113  0 
dm_crypt               22993  1 
acpi_call              12623  0 
binfmt_misc            17565  1 
joydev                 17606  0 
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
rfcomm                 47694  8 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
iwlagn                333717  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
iwlcore               167503  1 iwlagn
mac80211              294370  2 iwlagn,iwlcore
btusb                  18600  2 
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
dell_wmi               12681  0 
sparse_keymap          13898  1 dell_wmi
dell_laptop            13827  0 
dcdbas                 14438  1 dell_laptop
uvcvideo               72195  0 
psmouse                73535  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
serio_raw              13166  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178528  3 iwlagn,iwlcore,mac80211
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
i915                  514975  3 
drm_kms_helper         42136  1 i915
drm                   227495  4 i915,drm_kms_helper
xhci_hcd               77643  0 
ahci                   25951  2 
r8169                  48022  0 
libahci                26642  1 ahci
i2c_algo_bit           13400  1 i915
video                  19438  1 i915


/var/log/syslog at crash time:
> 
Aug 10 00:17:01 freefall CRON[3306]: (root) CMD (   cd / && run-parts --report /
etc/cron.hourly)
Aug 10 00:24:15 freefall kernel: imklog 4.6.4, log source = /proc/kmsg started.


kern.log says something similar, nothing in dmesg is bugging me. Really at a loss to what's causing it. Any suggestions at all where I should start looking?

---

### Post by Fallen_Demon on 2011-08-12
Ok, just happened again... Was running a VM this time. Seriously, has no one had an issue like this? Could it be that I've gone paranoid mode and encrypted /home?

EDIT: Can I get a mod to move this over to a general support or dev forum? I'd be really interested in helping fix this, just need a prod in the right direction

---

### Post by lbcra on 2011-09-02
I have exactly the same problem. I am kinda a lost as what to look for.
If some body can tell me where to look. I will do some investigation.

---

### Post by pyjamashark on 2011-09-20
ja - same thing happens to me, Im on a 32 bit natty - Dell XPS 15

---

### Post by mörgæs on 2011-09-20
Do you also get kernel panic in a live boot of 10.10?

---

### Post by Fallen_Demon on 2011-10-23
Upgrading to Oneiric fixed it. Not having any similar issues anymore, even after leaving it running for 3 days straight

---

