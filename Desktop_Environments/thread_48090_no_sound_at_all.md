---
title: "no sound at all"
date: 2005-07-11
forum: Desktop Environments
---

### Post by harm on 2005-07-11
Hi all,

I do not seem to get the audio of my fresh Ubuntu install to work. For testing I used rhytmbox on a mp3 stream but it errored 'Could not open resource for writing' and xmms which does not give any errors at all, it just won't play. Only when I select the esd output plugin I get the messege 'Could not play sound, check if your card is correctly configured etc.' Another thing I tried was System -> Preferences -> Sound -> Sound Events and playing a wav file there, no sound and no error. Ok first here the relevant information:

First determine soundcard $lspci | grep -i media
0000:02:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)

So I'm using an ensoniq es1371 which uses snd_ens1371.

Then did the correct modules loaded? $lsmod
snd_ens1371            22624  1
snd_rawmidi            22944  1 snd_ens1371
snd_seq_device          8332  1 snd_rawmidi
snd_ac97_codec         64608  1 snd_ens1371
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  1 snd_pcm
gameport                4608  1 snd_ens1371

(sorry for the layout)
So the correct modules are loaded.

The output of $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

In System -> Preferences -> Multi Media Selectors I have selected 'default sink' ESD and 'default source' OSS (test both fail with 'unable to construct test pipeline').

I'm dead in the water. Everything seems ok to me. Sound is not muted btw. I running on a Dell Optiplex GX1 PII 400MHz 158MB $uname -a 
Linux **** 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686 GNU/Linux
If people notice the small discrepency in using a 386 kernel on a 686 I tried switching to no avail.

Any help would be greatly appreciated!!!

PS I tried to get sound with Knoppix 3.6 and got the same results.

---

### Post by defkewl on 2005-07-11
Try opening : Applications > Sound & Video > Sound Control
Check if any output device is turned off (marked red)

Also try opening File > Preferences (from the same apps) to see what audio device you're using.

---

### Post by manicka on 2005-07-11
Do you have two sound cards by any chance. There has been some conflicts when there is a sound card on a system and an on-board one as well.

---

### Post by harm on 2005-07-11
Hmm, yes I do have two sound cards. On onboard and the card in my initial post is a pci card I plugged in after lspci didn't detected my onboard card. I had no way of checking what card this onboard thingy was or how to get it up and running. The 'isapnp' command is unknown on my system and I don't know where to find it. I did, however, turned the onboard card off in the BIOS. 

defkewl: I don't have  Applications > Sound & Video > Sound Control. I'm using Ubuntu Linux 5.04 : The Hoary Hedgehog and I'm not sure what you mean by your second remark. You mean in apps like xmms/rhytmbox? In xmms I tried using OSS/ALSA/ESD only ESD came up with an error the rest just didn't work (sometimes crashing xmms)

Edit: The GX1 uses a Crystal Semiconductor CS4236 for audio. Thanks to dell.com and their unsurpassed device db!

---

### Post by manicka on 2005-07-11
[QUOTE=harm] 
I don't have  Applications > Sound & Video > Sound Control. [/QUOTE]

Right click on the volume control icon and Open Volume Control

---

### Post by harm on 2005-07-11
Thanks I did just like you said and it lists under File > Change Device a TriTech id3 (OSS Mixer) and Ensoniq AudioPCI (ALSA Mixer). Both are clickable and seem responsive. But none can make xmms to run properly. Both output channels when on. Unfortunately.

---

### Post by harm on 2005-07-11
Update: I remove the second soundcard and booted with Knoppix. This resulted in a fine working sound system! You can't believe how happy I am. This, however, leaves me with the question how to get my card running in Ubuntu? Knoppix used the module cs4232 but doing $sudo modprobe cs4232 I get 
FATAL: Error inserting cs4232 (/lib/modules/2.6.10-5-386/kernel/sound/oss/cs4232.ko): No such device
Now what?

---

### Post by harm on 2005-07-11
I got it to work! It was the problem with the two sound cards. After fiddling about a bit  with the isa setting I finally have sound. Thanks all!

---

### Post by manicka on 2005-07-11
Enjoy!

---

### Post by filemanager on 2005-07-11
[QUOTE=harm]I got it to work! It was the problem with the two sound cards. After fiddling about a bit  with the isa setting I finally have sound. Thanks all![/QUOTE]
 Where is the ISA setting?

---

### Post by awol on 2005-08-07
[QUOTE=harm]I got it to work! It was the problem with the two sound cards. After fiddling about a bit  with the isa setting I finally have sound. Thanks all![/QUOTE]
 harm -
i have no audio on the same machine but no audio card - just onboard defaults. Can you say you have the onboard audio hardware working under Ubuntu504???? if so can you give stepwise instructions to get this - please?

---

