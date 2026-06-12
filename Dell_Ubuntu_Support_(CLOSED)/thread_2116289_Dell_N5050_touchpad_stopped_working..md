---
title: "Dell N5050 touchpad stopped working."
date: 2013-02-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rocketfish201 on 2013-02-15
On Ubuntu 12.04 I was able to turn off the touch pad using Fn+F3. I've since switched to Xubuntu 12.10, and for some reason that doesn't work. All of the other function keys work.

---

### Post by rocketfish201 on 2013-03-09
My Dell N5050's touchpad suddenly stopped working. 
I had turned my computer off the night before, and when I booted up this morning the touchpad wasn't being recognized. Under System Settings > Mouse and Touchpad there is a mouse tab, but not a touchpad tab.
 If I press Fn + F3 to turn the touchpad on or off the touchpad off notification pops up, [ATTACH=CONFIG]239967[/ATTACH], but it won't turn on.

---

### Post by varunendra on 2013-03-09
Threads merged.

Welcome to the forums rocketfish201!

Please do not create multiple threads on same issue. Feel free to bump your threads after 24 hours if they don't get attention you want.
Also, please confirm whether you are using Xubuntu or Ubuntu now, so I can edit the title as suitable.

---

### Post by rocketfish201 on 2013-03-09
Sorry, the threads weren't supposed to merge because they are for different topics. I had other issues with Xubuntu so I switched back to Ubuntu. However this morning my touchpad stopped working.

---

### Post by varunendra on 2013-03-09
Done, thanks!
The other thread could have attracted unnecessary attention while you no longer have that OS, so it was better to close or merge it, I did the latter :)

About your problem-

I think it may help if you post the outputs of -
```
xinput
lsmod
```
Make sure to post the outputs within 'Code' tags to preserve formatting (follow the 'example' link in my signature to see one).

---

### Post by rocketfish201 on 2013-03-09
```
joseph@joseph-laptop:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; reserved Dynex Watermelon Wireless Mice     id=10    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad            id=13    [slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                             id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Integrated Webcam                           id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]
```
```
joseph@joseph-laptop:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_idt      70774  1 
bnep                   18240  2 
rfcomm                 47562  0 
parport_pc             32867  0 
ppdev                  17114  0 
coretemp               13642  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
ghash_clmulni_intel    13221  0 
cryptd                 20531  1 ghash_clmulni_intel
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
snd_hda_intel          34117  3 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
microcode              23030  0 
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17391  0 
wmi                    19257  1 dell_wmi
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  530851  3 
wl                   3074942  0 
drm_kms_helper         49259  1 i915
drm                   290344  4 i915,drm_kms_helper
snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
psmouse               102075  0 
i2c_algo_bit           13565  1 i915
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
serio_raw              13216  0 
video                  19653  1 i915
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
lpc_ich                17145  0 
btusb                  22432  0 
cfg80211              208382  1 wl
bluetooth             211812  14 bnep,rfcomm,btusb
mei                    41410  0 
lib80211               14382  2 lib80211_crypt_tkip,wl
joydev                 17694  0 
mac_hid                13254  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
r8169                  62766  0 


```

---

### Post by varunendra on 2013-03-09
> **rocketfish201 said:**
> ```
joseph@joseph-laptop:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; reserved Dynex Watermelon Wireless Mice     id=10    [slave  pointer  (2)]
&#9116;   &#8627;[COLOR="#FF0000"]** AlpsPS/2 ALPS DualPoint TouchPad**[/COLOR]            id=13    [slave  pointer  (2)]


```

Not sure which driver this one uses, let's just try a generic one. Please run -
```
sudo modprobe -rfv psmouse
```
watch out for errors. Post back if there are any. Then run -
```
sudo modprobe -v psmouse
```
Post back the result.

---

### Post by rocketfish201 on 2013-03-09
```
rmmod /lib/modules/3.5.0-25-generic/kernel/drivers/input/mouse/psmouse.ko
```
```
insmod /lib/modules/3.5.0-25-generic/kernel/drivers/input/mouse/psmouse.ko 
```

---

### Post by varunendra on 2013-03-09
That's normal. Did it make the touchpad work ?

If not, disable dell-wmi for a test -
```
sudo modprobe -rfv dell_wmi
```
..then run the previous two commands once more. See if it helps.

---

### Post by rocketfish201 on 2013-03-09
Still not working.

---

### Post by varunendra on 2013-03-09
Hmm.. that's the end of logical solutions I have at the moment. We may try something wilder if you wish (or better, wait for input by someone who knows what they are doing).

If you wish to try, first make sure it is not going to break your system (if it does, a restart will fix it as it will be temporary) -
```
sudo modprobe -rfv dell-laptop
sudo modprobe -rfv dell-wmi
sudo modprobe -rfv psmouse
sudo modprobe -v psmouse
```
Post back if there are any error messages.
If the laptop starts behaving funny after any of the above commands (although it shouldn't), just reboot and everything will be reverted by itself.

However, if the above commands make no difference (positive or negative), then do the following-
```
echo -e "\nblacklist dell-wmi\nbalcklist dell-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot, and see if the touchpad works.

Be aware that disabling dell-wmi may disable some special Fn+ key combinations. We are only testing if any of these two drivers is causing the problem.

---

### Post by rocketfish201 on 2013-03-09
I just went ahead and reinstalled Ubuntu. Not the fix I was hoping for, but at least the touchpad works.

---

### Post by varunendra on 2013-03-09
> **rocketfish201 said:**
> I just went ahead and reinstalled Ubuntu. Not the fix I was hoping for, but at least the touchpad works.

Well.. if you have no apps and settings to save, then of course reinstallation is quicker, and quicker is better :)

---

