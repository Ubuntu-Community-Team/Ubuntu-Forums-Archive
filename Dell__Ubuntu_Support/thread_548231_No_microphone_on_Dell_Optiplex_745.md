---
title: "No microphone on Dell Optiplex 745"
date: 2007-09-11
forum: Dell  Ubuntu Support
---

### Post by mschering on 2007-09-11
Hi All,

Sorry for another micorphone thread but I couldn't find a suitable answer.

I have a Dell Optiplex 745 with onboard intel sound. I have ubuntu 7.04 installed. The lspci output:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

The following modules are loaded:

mschering@mschering-desktop:~$ lsmod | grep snd
snd_hda_intel         262552  2 
snd_pcm_oss            44800  1 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35200  0 
snd_seq_midi            9728  0 
snd_rawmidi            25984  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54128  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56452  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  2 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm



All my mixer channels are enabled. I've been trying lots of things.

An interesting thing to note. The line-in and headphone output are combined on this piece of hardware.

Does anyone know how to fix this?

Thanks,
Merijn

---

### Post by linuxwizard on 2007-09-11
Check over these
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

---

### Post by mschering on 2007-09-11
Thanks, but I already tried that with no results. 

It even gave me another problem. My volume control applet and keyboard volume controls don't work anymore after I manually installed alsa 1.14.

---

### Post by linuxwizard on 2007-09-11
Have you installed the latest Ubuntu updates ? Have seen issues with kernel. You might want to look on Launchpad see if any bugs has been reported. Check for sound card or issue with mic.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20)

---

