---
title: "Low sound volume on Dell Studio 1535"
date: 2009-03-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mike998 on 2009-03-11
I have a dell studio 1535 that I have installed both Intrepid and Jaunty on (Intrepid 32 and 64 bit and Jaunty 64 bit) and have found that the sound volume seems to be very low.
I actually have to crank the volume of both main and the application running in order to hear anything going on.

Is there any other Studio owner encountering this problem?

I forgot to mention I have tried switching alsa and oss, I even tried installing pulse-audio.  Audio works, but it's low and lower than it ever was when I was using Vista.

---

### Post by n6yga on 2009-03-12
I have a brand new Dell Studio XPS1340 and I am having the same problems. Very low sound! Otherwise, these are very good laptops.

Hopefully, one of us will find the problem!

Mark.

---

### Post by superm1 on 2009-03-12
> **n6yga said:**
> I have a brand new Dell Studio XPS1340 and I am having the same problems. Very low sound! Otherwise, these are very good laptops.

Hopefully, one of us will find the problem!

Mark.
Open up your audio mixer, and make sure you turn up Master, PCM, and Front.  The combination of all 3 sets your volume.

---

### Post by n6yga on 2009-03-12
Actually, it's a bug in Alsa version 1.16.

The fix is here and it worked for me:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Mark.

---

### Post by mike998 on 2009-03-19
Apoligies for the delay in replying...
I did try this and there was no real improvement.
I'm just going to deal with the quiet sound.

---

### Post by thunderdan on 2009-03-26
I have an Inspiron 1525 that came with Ubuntu 8.04 installed on it. I also have the low volume problem. I tried OpenSUSE and it was much louder.

---

### Post by n6yga on 2009-03-26
I guess you could just wait until 9.04.

I have alpha 6 running on my 1340 now and it worked out of the box.



Mark

---

### Post by eldersoares on 2009-05-22
i had the same problem, the same notebook, and it was solved increasing the "front" volume, that was set to 70%

$: amixer set Front 100%

---

### Post by crfvendramini on 2009-05-22
Hi

I have a Inspiron 1525 and the overall sound quality seems to be fine now.

Some useful informations about each system might can help. Next follows specific data  about my Inspiron 1525  current system sound configuration.   

**1. Installed version of ALSA (*1):**

```
$ alsactl -v
alsactl version 1.0.20
```[B]

2. Sound card model (*2):[/B]

```
$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant ID 2c06
Codec: Silicon Image SiI1392 HDMI
Codec: **SigmaTel STAC9228**
```**3. ALSA modules loaded:**

```
$ lsmod | grep snd
snd_hda_codec_idt      78476  1 
snd_hda_codec_intelhdmi    22272  1 
snd_hda_intel          38536  6 
snd_hda_codec          93696  3 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel
snd_hwdep              17032  1 snd_hda_codec
snd_pcm_oss            51872  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                98568  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            40320  0 
snd_seq_midi_event     16640  1 snd_seq_oss
snd_seq                66848  4 snd_seq_oss,snd_seq_midi_event
snd_timer              33168  3 snd_pcm,snd_seq
snd_seq_device         16532  2 snd_seq_oss,snd_seq
snd                    82760  23 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18960  2 snd_hda_intel,snd_pcm
```(*1) Compiled by myself.
(*2) I found that model at [HD-Audio-Models.txt]("http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt") and then inserted the following line at the end of the file "/etc/modprobe.d/alsa-base.conf":

```
$ cat /etc/modprobe.d/alsa-base.conf
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
**options snd-hda-intel model=dell-bios**
```

---

### Post by louca on 2009-06-19
> **eldersoares said:**
> i had the same problem, the same notebook, and it was solved increasing the "front" volume, that was set to 70%

$: amixer set Front 100%

Worked for me.

I'm on a Dell Studio 1555.

---

### Post by harry2006 on 2009-08-04
thanks a lot..had the same problem,,,just added the line mentioned and its working fine...

---

### Post by skattorshot on 2009-08-28
adjust the front volume worked for me too, thanks eldersoares!

---

