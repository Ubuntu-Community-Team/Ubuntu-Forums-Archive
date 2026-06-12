---
title: "Optiplex GX260 Sound problems"
date: 2007-07-10
forum: Dell  Ubuntu Support
---

### Post by doozy on 2007-07-10
Hi all. It's good to join the Ubuntu users. Just loaded up my first Linux PC with Desktop Ubuntu 7.04, and so far so good. One exception is the sound / audio I can't get working.

Doesn't seem to be any problems in xWindows and from Terminal I get following. Any help glady appreciated, be gentle I am a newbie to Linux....

From another thread I found these commands:

**Open a terminal and type "lspci" (without the quotes). Also type "lsmo**d"

Intel 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4

The output is: 

lspci:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)


lsmod | grep snd 


snd_hda_intel          22040  0 
snd_hda_codec         205184  1 snd_hda_intel
snd_intel8x0           34332  1 
snd_ac97_codec         97952  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44416  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  5 snd_hda_intel,snd_hda_codec,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52464  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    53892  14 snd_hda_intel,snd_hda_codec,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11016  3 snd_hda_intel,snd_intel8x0,snd_pcm

---

### Post by rrinker on 2007-07-11
My sound worked immediately after an install. Then the other day I noticed it seemed to have stopped working. I don't have speakers plugged in, just a headset with mic. At first I thought the cat hoppign behind the computer pulled the plug, but no, it was securely plugged in. In each multimedia app I tried I got messages saying the hardware wasn't found or no device was available. I tried changing the audio devices (it was all set on 'Auto') to no avail, no matter what I picked, it would not play any sounds. I finally gave up and switched it all back to Auto and restarted - the sound came back and has been working since. I have no idea what may have caused it to stop in the first place.

                         --Randy

---

### Post by doozy on 2007-07-15
I'm still getting nowhere fast with the sound issue.

I might try a fresh install from the Dasktop CD, as my original newbie mistake was installing the Server version, and then enabling the desktop build on top of that.

Not sure if that makes logical sense as I don't know enough about the different versions to say whether sound would be an issue from the Server install to Desktop add on.

Will try and let you know.

Also just added a 4-port KVM and since then Ubuntu only allows you to set a 640x480 !! ??

Big learning curve comes with Ubuntu, but I haven't given up just yet. ;-p

---

### Post by luvit on 2008-03-13
i had success with 7.10 alternate image and ensuring everything was unmuted in the large volume control panel :)
the alternate image also allowed full optimal support of the integrated video card. I placed the GX260's latest BIOS in my blog.

---

### Post by stream303 on 2008-03-14
This might sound very strange, but back when I had a GX250, I found that the line output and headphone outputs were reversed!  It was a drag to use the headphones from the rear panel, and the speaker attachment to the front. :)

Drove me nuts.

---

### Post by Fanless_Puppy_Fan on 2008-03-15
> **stream303 said:**
> This might sound very strange, but back when I had a GX250, I found that the line output and headphone outputs were reversed!  It was a drag to use the headphones from the rear panel, and the speaker attachment to the front. :)

Drove me nuts.

Two plugs on the mobo could fix it. Sometimes you just have to crack the case.   <---- double entendre

---

