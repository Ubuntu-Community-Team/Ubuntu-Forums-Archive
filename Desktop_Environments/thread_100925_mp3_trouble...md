---
title: "mp3 trouble.."
date: 2005-12-08
forum: Desktop Environments
---

### Post by windowsXuser on 2005-12-08
I am having trouble getting my mp3 files to get sound.

I have installed the gstreamer package and have used easy breezy to install some multimedia packages.

I have tried kaffeine and installed kaffeine-xine and the w32 codecs with it.  I have also tried XMMS, but no luck.

Does it have something to do with my audio drivers.  in system settings under multimedia - harware i have it set to autodetect my audio card, but havent updated my drivers.  Not sure if thats my problem or not.  I have read some of the other threads, but still cant get it working.

any help would be appreciated.

blair..

---

### Post by windowsXuser on 2005-12-08
just did a lspci to see if my audio card it detected and it looks like it seems my sound blaster live audio card.


blair@ubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 44)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
0000:00:09.0 USB Controller: OPTi Inc. 82C861 (rev 10)
0000:00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:00:0b.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
0000:00:0d.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 11

---

### Post by mlomker on 2005-12-08
Is this sound in MP3's or no sound in general?  Do you get system sounds or anything else?

I assume you've gone into kmix and looked at the settings in there?  amaroK uses the PCM output in kmix on my machine.

---

### Post by windowsXuser on 2005-12-08
alright, so i figured it out.

just went into XMMS options-preferences and changed my output plugin to ALSA and changed my video card to SB LIVE.

works like a dream..

---

