---
title: "No sound all of a sudden! Strange!"
date: 2005-10-29
forum: Desktop Environments
---

### Post by otis_u on 2005-10-29
Hi,

I've always had samplerate issues with my on board via audio. Usually get it working after a little tweaking here and there.

It was working fine just an hour ago... all of a sudden: NOTHING!
I've tried lots of basic clicking around, but I really don't know what's wrong.

However, I get this error message when restarting the sound system from within the Sound and Multimedia control panel:

> Sound server informational message:
Error while initializing the sound driver:
device: 0 can't be opened for playback (No such file or directory)
The sound server will continue, using the null output device.


When I go into the sound section of KInfoCenter I have this under Audio Devices:
> 0: VIA 8235 (DUPLEX)

I would really appreciate any help you have- thank you!

---

### Post by beefsprocket on 2005-10-29
Any details on what transpired during that hour? Have you upgraded packages, changed kernels, etc? I'd imagine you've tried rebooting? Is your sound module loading? What shows up if you try "lsmod |grep snd"? How about "dmesg |grep VIA"?

I've had a hard time with the same sound card in most distros -- hoary was the first that seemed to get the hardware channels configured correctly.

---

### Post by otis_u on 2005-10-29
I have somewhat random samplerate problems. One second I'm sounding fine, other times it seems like the application is trying to play at 44100 instead of 48000 [buzz-y harsh garbled sound], so when that happens my first [and usually successful] reaction is to enable or disable the 'custom rate: 48000' box in the sound &  multimedia panel.

I started up a video game [that previously worked fine] and was getting the samplerate problem. Left the game to go change the samplerate in the sound & multimedia panel, applied the change... No sound! Anywhere!

Many reboots and a few hours tinkering later I still have no sound and decided to post here.

Here is the result of **lsmod |grep snd**:
> 
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  0
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  11 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd


And here is the result of **dmesg |grep VIA**

> 
[4294675.078000] uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294675.143000] uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
[4294675.240000] ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
[4294675.305000] eth0: VIA Rhine II at 0x1e400, 00:30:1b:25:a1:87, IRQ 11.
[4294703.099000] agpgart: Detected VIA KT266/KY266x/KT333 chipset


Anything stick out?

---

### Post by beefsprocket on 2005-10-29
Hmm, looks like you have the proper modules loaded. Have you tried running alsamixer to see if changing the samplerate muted a channel or two? I'll try to find the alsa page that lets you set the hardware channels -- iirc the harshness and lack of /dev/dsp is mentioned in a howto on the alsa site.

Edit: check this post (and page in general) [http://www.mepis.org/node/1499#comment-23058]("http://www.mepis.org/node/1499#comment-23058"). 
Also take a look at the alsa page for the card: [http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=via82xx]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=via82xx")
Seems you might want to apt-get the alsa-utils/tools package(s) and run alsaconf. I'll poke around my hdd for notes I wrote the last time I fought with the card.

---

### Post by otis_u on 2005-10-30
[QUOTE=beefsprocket]Hmm, looks like you have the proper modules loaded. Have you tried running alsamixer to see if changing the samplerate muted a channel or two? I'll try to find the alsa page that lets you set the hardware channels -- iirc the harshness and lack of /dev/dsp is mentioned in a howto on the alsa site. [/quote] 

Agh!
The 'headphone' channel was muted.

I didn't realize that the main output was considered 'headphone'.

I feel like an idiot and greatly appreciate your help, haha.

In order to repay my debt of wasting your time, I'm going to write a helpful post on how I got my Ralink 2500 chipset wireless card working.

Thanks again.

---

