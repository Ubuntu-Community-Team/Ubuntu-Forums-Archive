---
title: "Problem with skype on Dell vostro 1400"
date: 2009-03-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by whatvn on 2009-03-29
Hi all, 
I have a Dell Vostro 1400 running Ubuntu 8.10, everything works well but Skype.
I cannot make call using skype, the problem is I can hear what people says but they dont hear what I say. I've tried many solutions through Google, this forum and Skype forum, but no way.

Here is some info:
lspci output 
```
lspci | grep Audio
 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
 
```
to make sure that my laptop only has 1 audio card (82801H intel)
> less /proc/asound/modules
  0 snd_hda_intel
alsa mixer show there's no device muted, I also set sound option in skype sounds option to everything, pulse, hw intel..., got same result.

Here is alsabase content

```
cat alsa-base
 # autoloader aliases
 install sound-slot-0 /sbin/modprobe snd-card-0
 install sound-slot-1 /sbin/modprobe snd-card-1
 install sound-slot-2 /sbin/modprobe snd-card-2
 install sound-slot-3 /sbin/modprobe snd-card-3
 install sound-slot-4 /sbin/modprobe snd-card-4
 install sound-slot-5 /sbin/modprobe snd-card-5
 install sound-slot-6 /sbin/modprobe snd-card-6
 install sound-slot-7 /sbin/modprobe snd-card-7
 
 # Cause optional modules to be loaded above generic modules
 install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
 install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
 install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
 install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
 install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
 install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
 # Cause optional modules to be loaded above sound card driver modules
 install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
 install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
 
 # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
 install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
 
 # Load snd-seq for devices that don't have hardware midi;
 #   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
 #   non-Creative Labs PCI hardware
 install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
 # Prevent abnormal drivers from grabbing index 0
 options bt87x index=-2
 options cx88_alsa index=-2
 options saa7134-alsa index=-2
 options snd-atiixp-modem index=-2
 options snd-intel8x0m index=-2
 options snd-via82xx-modem index=-2
 options snd-usb-audio index=-2
 options snd-usb-usx2y index=-2
 options snd-usb-caiaq index=-2
 # Ubuntu #62691, enable MPU for snd-cmipci
 options snd-cmipci mpu_port=0x330 fm_port=0x388
 # Keep snd-pcsp from beeing loaded as first soundcard
 options snd-pcsp index=-2

```

blacklist content```

cat blacklist
 # This file lists those modules which we don't want to be loaded by
 # alias expansion, usually so some other driver will be loaded for the
 # device instead.
 
 # evbug is a debug tool that should be loaded explicitly
 blacklist evbug
 
 # these drivers are very simple, the HID drivers are usually preferred
 blacklist usbmouse
 blacklist usbkbd
 
 # replaced by e100
 blacklist eepro100
 
 # replaced by tulip
 blacklist de4x5
 
 # causes no end of confusion by creating unexpected network interfaces
 blacklist eth1394
 
 # snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
 # hardware on its own (Ubuntu bug #2011, #6810)
 blacklist snd_intel8x0m
 
 # Conflicts with dvb driver (which is better for handling this device)
 blacklist snd_aw2
 
 # causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
 blacklist i2c_i801
 
 # replaced by p54pci
 blacklist prism54
 
 # replaced by b43 and ssb.
 blacklist bcm43xx
 
 # most apps now use garmin usb driver directly (Ubuntu: #114565)
 blacklist garmin_gps
 
 # replaced by asus-laptop (Ubuntu: #184721)
 blacklist asus_acpi
 
 # low-quality, just noise when being used for sound playback, causes
 # hangs at desktop session start (Ubuntu: #246969)
 blacklist snd_pcsp
```
 
lsmod
```

lsmod | grep snd
 snd_hda_intel         384176  4 
 snd_pcm_oss            46848  0 
 snd_mixer_oss          22784  1 snd_pcm_oss
 snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
 snd_seq_dummy          10884  0 
 snd_seq_oss            38528  0 
 snd_seq_midi           14336  0 
 snd_rawmidi            29824  1 snd_seq_midi
 snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
 snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
 snd_timer              29960  2 snd_pcm,snd_seq
 snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
 snd                    63268  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
 soundcore              15328  1 snd
 snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
 
```

I run skype on terminal and got these errors:

```
 skype
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
 
 RtApiAlsa: underrun detected.

```
the last line appeared when I use skype echo test. I don't have any bluetooth device, and dont know what these errors mean?

Hope someone can help me solve this problem, I've tried many times with many solutions, very tired.
Regard!

---

### Post by khelben1979 on 2009-03-29
Okay, have you tried to download the version which uses a static version of the QT library? You'll find it [here]("http://www.skype.com/go/getskype-linux-static").

Maybe it's worth a try?

---

### Post by whatvn on 2009-03-30
Hi khelben1979,
Thank you for reading, I installed QT library static version before.
I fixed this problem last night, remove all configuration and config all again. I really don't remember what I did, but Skype works.
Regard!

---

### Post by Sylslay on 2009-04-20
tApiAlsa: underrun detected.


RtApiAlsa: underrun detected.
Faound the some problem on Juanty 9.04

RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.

---

