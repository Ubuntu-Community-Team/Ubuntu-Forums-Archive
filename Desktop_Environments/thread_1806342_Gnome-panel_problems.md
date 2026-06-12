---
title: "Gnome-panel problems"
date: 2011-07-17
forum: Desktop Environments
---

### Post by Theredbaron1834 on 2011-07-17
I have been getting video error's in gnome-panel since I upgraded to Natty. It seems to become transparent on part of it, and my background covers it. I have tried deleting my gnome-panel preference's, to no aval. Does anybody know how to fix this?

[IMG]http://img143.imageshack.us/img143/2779/screenshottjy.png[/IMG]

[IMG]http://img594.imageshack.us/img594/2130/screenshot1xb.png[/IMG]

---

### Post by sky5564 on 2011-07-17
Just right click on the transparent part then click background and set the transparency level from there.

---

### Post by Theredbaron1834 on 2011-07-17
I don't have any transparency set. I just use system theme, Hanso right now. I changed to solid color, set to opaque and changed back. I hope that fixes it.

Nope, tried it and it still overlaps the panel. Could it be a problem with my xserver?

---

### Post by wildmanne39 on 2011-07-17
Hi, run these commands in a terminal
```
sudo lshw
```
```
lsmod
```
```
/usr/lib/nux/unity_support_test -p
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by Theredbaron1834 on 2011-07-17
sudo lsmod
```
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
dm_crypt               22463  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
arc4                   12473  2 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
ath5k                 144412  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
rfcomm                 38125  12 
snd_seq_midi_event     14475  1 snd_seq_midi
sco                    17827  2 
bnep                   17785  2 
ppdev                  12849  0 
l2cap                  48656  16 rfcomm,bnep
binfmt_misc            13213  1 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
parport_pc             32111  0 
snd_timer              28659  2 snd_pcm,snd_seq
btusb                  18160  2 
uvcvideo               66851  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
cfg80211              156212  3 ath5k,ath,mac80211
psmouse                73312  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
eeepc_laptop           19417  0 
sparse_keymap          13666  1 eeepc_laptop
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
i915                  450934  2 
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  1 
uas                    17676  0 
drm_kms_helper         40745  1 i915
drm                   180037  3 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915

```

lsmod
```
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
dm_crypt               22463  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
arc4                   12473  2 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
ath5k                 144412  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
rfcomm                 38125  12 
snd_seq_midi_event     14475  1 snd_seq_midi
sco                    17827  2 
bnep                   17785  2 
ppdev                  12849  0 
l2cap                  48656  16 rfcomm,bnep
binfmt_misc            13213  1 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
parport_pc             32111  0 
snd_timer              28659  2 snd_pcm,snd_seq
btusb                  18160  2 
uvcvideo               66851  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
cfg80211              156212  3 ath5k,ath,mac80211
psmouse                73312  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
eeepc_laptop           19417  0 
sparse_keymap          13666  1 eeepc_laptop
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
i915                  450934  2 
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  1 
uas                    17676  0 
drm_kms_helper         40745  1 i915
drm                   180037  3 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915

```

/usr/lib/nux/unity_support_test -p
```
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  1.4 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

```

Though, according to Ubuntu Tweak, I am not using unity's wm. I am using compiz. Could it be a compiz problem?

---

### Post by wildmanne39 on 2011-07-18
Hi, it probably is compiz, here is a link for people using compiz in classic mode.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

---

### Post by Theredbaron1834 on 2011-07-18
Thanks, doing that now. I hope this fixes everything.

---

### Post by wildmanne39 on 2011-07-18
> **Theredbaron1834 said:**
> Thanks, doing that now. I hope this fixes everything.Hi, me too, if you have other problems let us know.

---

### Post by Theredbaron1834 on 2011-07-18
:( Didn't work.
Any other idea's, or is this something I will have to live with. It doesn't stop much usability, just really annoying. The only problem is when it blocks my notification's.

---

### Post by wildmanne39 on 2011-07-18
> **Theredbaron1834 said:**
> :( Didn't work.
Any other idea's, or is this something I will have to live with. It doesn't stop much usability, just really annoying. The only problem is when it blocks my notification's.Hi, to be honest I am not sure, with your video card driver I have not seen people have much problems.

First log out and click on your username then go to the bottom of the screen choose ubuntu classic with the no effects and see if that fixes the issue.

---

### Post by Theredbaron1834 on 2011-07-19
That doesn't work either.

---

### Post by wildmanne39 on 2011-07-19
> **Theredbaron1834 said:**
> That doesn't work either.
Hi, I am out of ideas on this one hopefully someone will jumped in here with an idea.

---

### Post by Theredbaron1834 on 2011-07-19
Yeah, thanks for trying. I really appreciate it.

---

### Post by wildmanne39 on 2011-07-19
> **Theredbaron1834 said:**
> Yeah, thanks for trying. I really appreciate it.
Hi, you are very welcome!!

---

