---
title: "Didn't anticipate all the complication"
date: 2009-01-12
forum: General Help
---

### Post by Wicksam36 on 2009-01-12
I didn't really do much research into it before I installed Ubuntu 8.10, I just simply wanted a new OS.  I don't like Windows. I had no idea I wouldn't be able to use my wireless or get the sound to work on my computer. 

I have a linksys router for my wireless network, and I have an internal 802.11b/g wireless card.  Ubunutu recognizes the network I am trying to connect to, but it just won't connect even with the correct pass key.  I believe this may be a bug.  Is there anyway to fix this?

Another thing is is that I can't get sound.  I downloaded all the codecs and made sure nothing was muted, but my speakers make a hissing sound...and that's the only sound they will make.  It's all very frustrating.  It currently doesn't put Linux in a very good light for me. No internet and no music...the two things I love most in the word!


Any help would be very appreciated. :-)

---

### Post by wolfen69 on 2009-01-12
in terminal, do:
```
lspci
``` and post the output here. also remember that ubuntu isn't the only linux around. sometimes just changing to another distro cures all ills. (fedora, open suse, mandriva are 3 big ones) don't give up quickly. it will be worth your time. but first let's try to get your problems fixed.

---

### Post by Wicksam36 on 2009-01-12
> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
03:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
04:06.0 Communication controller: Conexant Systems, Inc. Device 2f40

...

---

### Post by Slim Odds on 2009-01-12
I don't see a wireless device in that list.....

---

### Post by Wicksam36 on 2009-01-12
Hmmmm...well, I must have something.  I did have wireless on Windows that worked just fine, so I don't know.  I am "demoing" Fedora right now and I have the same wireless problems as Ubuntu.

---

### Post by hangfire on 2009-01-12
> **wolfen69 said:**
> in terminal, do:
```
lspci
``` and post the output here. also remember that ubuntu isn't the only linux around. sometimes just changing to another distro cures all ills. (fedora, open suse, mandriva are 3 big ones) don't give up quickly. it will be worth your time. but first let's try to get your problems fixed.

Please give us the brand and model of your laptop, the brand and model of your wireless adapter, also your sound chip. You should be able to find most of this information in your invoice.

Please post the output of:

```
lsmod | grep snd
```

-HF

---

### Post by Wicksam36 on 2009-01-12
I have a desktop.  It's a Gateway GT5694.  Realtek RTL8187B Wireless 802.11g 54Mbps Network Adapter is my wireless.  HDA ATI SB is my soundcard (I think).  

Results for lsmod | grep snd:

> snd_hda_intel         489264  3 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_seq_dummy          11524  0 
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm


---

### Post by robobot on 2009-01-12
I have the same motherboard chipsets and audio device as you, and my sound has been working fine since 8.04. However, it only works with ALSA. Try going to your mixer/volume control and selecting the "HDA ATI SB (Alsa mixer)" device as your audio device. Also, try turning up the volume. The sound playback in Ubuntu is quieter than the sound playback in Windows on this device.

Regarding the wireless networking, if your computer is finding the access point and attempting to connect, your wireless card is being detected, and you likely do have usable drivers installed already. Try checking that your computer and your router are trying to use the same type of encryption.

---

