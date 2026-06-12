---
title: "No Sound OptiPlex GX260 Intel 82801EB/ER"
date: 2010-02-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DaleEMoore on 2010-02-18
Windows got good sound but I got tired of futzing with viruses and malware so I switch to Ubuntu 9.10. I LOVE IT; but, I can't figure out how to make any sound happen on my Dell OptiPlex GX260 with Intel 82801EB/ER.

Any help you can provide is very much appreciated,
Dale E. Moore

---

### Post by DaleEMoore on 2010-02-18
Would someone point me in a diagnostic methodology or procedure direction please?

---

### Post by DaleEMoore on 2010-02-19
root@desktop:~# lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by DaleEMoore on 2010-02-19
root@desktop:~# dmesg| grep 8x0
[   10.708025] intel8x0_measure_ac97_clock: measured 52166 usecs (2514 samples)
[   10.708031] intel8x0: clocking to 48000

---

### Post by DaleEMoore on 2010-02-19
root@desktop:~# lsmod | grep snd
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm

---

### Post by DaleEMoore on 2010-02-19
user@desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by DaleEMoore on 2010-02-19
Attached is the output from the following:

user@desktop:~$ pulseaudio -vvvv >pulseaudio3.txt 2>&1

there seem to be lots of errors, but; I'm unsure what my next step is.

---

### Post by DaleEMoore on 2010-02-19
user@desktop:/usr/lib/openoffice/basis3.1/share/gallery/sounds$ aplay /usr/lib/openoffice/basis3.1/share/gallery/sounds/ok.wav

hangs.

UPDATE: Oops, it wasn't hanging... after a while I got:
Playing WAVE '/usr/lib/openoffice/basis3.1/share/gallery/sounds/ok.wav' : Signed 16 bit Little Endian, Rate 11025 Hz, Mono

Bit I did not hear any sound.

---

### Post by DaleEMoore on 2010-02-19
I'm wondering what the next step might be...

---

### Post by DaleEMoore on 2010-02-20
Any help at all would be very much appreciated.

---

### Post by DaleEMoore on 2010-02-20
gnome-control-panel
Hardware, Sound
Waiting for sound system to respond
50 minutes later still no response

PulseAudio Preferences do not appear in gnome-control-panel, Other.

---

### Post by DaleEMoore on 2010-02-20
Perhaps it is a good idea to submit this as a bug to LaunchPad? This [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) is the suggested LaunchPad submission process.

Though, since aplay is not working, perhaps upgrading to the latest ALSA as described here [http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/) is the next proper step?

---

### Post by zsitvaij on 2010-02-20
Instead of following the instructions of that blogpost, a better idea would be to add ppa:ubuntu-audio-dev/ppa to your software sources, as it's maintained and kept up to date by the actual ubuntu devs.

---

