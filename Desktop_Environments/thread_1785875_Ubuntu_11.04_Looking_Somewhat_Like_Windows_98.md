---
title: "Ubuntu 11.04 Looking Somewhat Like Windows 98"
date: 2011-06-18
forum: Desktop Environments
---

### Post by gggccc on 2011-06-18
I don't know what is causing this problem.

I have spent the last couple hours Googleing the problem, to no avail.

All of my icons look strange and parts of the UI look strange also. 

Here is a picture of the bar at the top of the screen:
[IMG]http://i.imgur.com/fTtaD.png[/IMG]

Here is a picture of folders on my computer:
[IMG]http://i.imgur.com/ilbGb.png[/IMG]

I do have the latest nVidia GFX card drivers installed.

For the first few seconds after I boot, everything looks normal, but it almost immediately switches to looking like this.

I really would appreciate any help I could get.

Thanks!

---

### Post by silex89 on 2011-06-18
That's the result I had on a virtual machine running the Vesa Driver.... :S your NVidia card wasn't detected or some package got broken during the installation......

Hummmm. Try running lsmod and post the output.


Best luck :)

---

### Post by gggccc on 2011-06-18
> **silex89 said:**
> That's the result I had on a virtual machine running the Vesa Driver.... :S your NVidia card wasn't detected or some package got broken during the installation......

Hummmm. Try running lsmod and post the output.


Best luck :)

```
Module                  Size  Used by
aesni_intel            55161  2 
cryptd                 20510  1 aesni_intel
aes_x86_64             17208  1 aesni_intel
aes_generic            38279  2 aesni_intel,aes_x86_64
nls_iso8859_1          12713  2 
nls_cp437              16991  2 
vfat                   21708  2 
fat                    61374  1 vfat
rfcomm                 47694  8 
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
sco                    18131  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
joydev                 17606  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
btusb                  18600  2 
bluetooth              72448  9 rfcomm,sco,bnep,l2cap,btusb
snd_hda_codec_hdmi     28103  1 
usblp                  18233  0 
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
snd_usb_audio         112426  1 
v4l2_compat_ioctl32    17078  1 videodev
snd_usbmidi_lib        25139  1 snd_usb_audio
nvidia              11989520  40 
snd_hda_codec_realtek   336693  1 
rt2860sta             543010  0 
arc4                   12529  2 
rt2800pci              18535  0 
rt2800lib              45181  1 rt2800pci
crc_ccitt              12667  2 rt2860sta,rt2800lib
rt2x00pci              14322  1 rt2800pci
rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci
snd_seq_midi           13324  0 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
snd_hda_intel          33211  2 
mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib
usb_storage            53538  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi_event     14899  1 snd_seq_midi
uas                    17996  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
eeepc_wmi              19323  0 
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178528  2 rt2x00lib,mac80211
snd_pcm                96625  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
sparse_keymap          13898  1 eeepc_wmi
snd_timer              29602  2 snd_seq,snd_pcm
snd                    67382  18 snd_hda_codec_hdmi,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_seq,snd_hwdep,snd_seq_device,snd_pcm,snd_timer
eeprom_93cx6           12725  1 rt2800pci
xhci_hcd               77643  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73535  0 
serio_raw              13166  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
ahci                   25951  1 
crc_itu_t              12707  1 firewire_core
r8169                  48022  0 
libahci                26642  1 ahci

```

---

### Post by Krytarik on 2011-06-18
Have a look at these links:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

Recent threads with summed-up workarounds:
[http://ubuntuforums.org/showthread.php?t=1722179](http://ubuntuforums.org/showthread.php?t=1722179)
[http://ubuntuforums.org/showthread.php?t=1724702](http://ubuntuforums.org/showthread.php?t=1724702)

Here is another, most recent, workaround that may work:
[http://ubuntuforums.org/showthread.php?p=10800526#post10800526](http://ubuntuforums.org/showthread.php?p=10800526#post10800526)

Greetings.

---

### Post by gggccc on 2011-06-19
I can't see if those will fix my problem right now(on phone), but I'll be sure to check them out ASAP and mark the thread solved if one of em works. 

Thanks for helping :)

---

