---
title: "Creative Soundblaster Xtreme Gamer Issues"
date: 2009-06-03
forum: General Help
---

### Post by lake54 on 2009-06-03
I have just upgraded to 9.04 from a virgin 8.10 install - sound didn't work then, it still doesn't now.

I've tried the official Creative drivers from their site, but still no sound.

I then tried the guide here: [https://help.ubuntu.com/community/OpenSound#Installing%20Prerequisite%20Packages]("https://help.ubuntu.com/community/OpenSound#Installing%20Prerequisite%20Packages")

and it worked!

But, stupid me, I then carried on, with the DEB package bit. And it broke. Again.

Any ideas on how to get my sound back?

I'm a Linux noob, so any terminal stuff you'll have to do step-by-step. I do have some (limited) experience though.

Thanks!

James

Oh, also:

lspci gives me this:

> 00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:05.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
05:06.0 Multimedia audio controller: Creative Labs SB X-Fi
05:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)


and aplay -l gives me this:

> **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: XFi [Creative X-Fi], device 0: X-Fi 20k1 [WaveOut/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7


---

### Post by lake54 on 2009-06-03
By the way, the ubuntu-uk mailing list guys have suggested a clean install of 9.04

I'd rather try some alternate methods first.

---

### Post by lake54 on 2009-06-03
Anyone?

---

### Post by lake54 on 2009-06-03
Someone must have a solution!

---

### Post by davideotape on 2009-06-04
At the moment audio in linux is a bit of a mess (see attached diagram) Try a fresh install of 9.04. These might help:

[http://ubuntuforums.org/showthread.php?t=239981](http://ubuntuforums.org/showthread.php?t=239981)
[http://www.fusetext.com/2009/05/ubuntu-linux-creative-sound-blaster-x-fi-driver-installation-how-to/](http://www.fusetext.com/2009/05/ubuntu-linux-creative-sound-blaster-x-fi-driver-installation-how-to/)

---

### Post by lake54 on 2009-06-04
Hey Manchester as well :-)

That second link looks quite useful - I'll see what I can rummage around with from that ;-)

Lake54

---

### Post by propagation_of_sound on 2009-06-05
Hi james. (David getting in there too early!)

Right. Go into Sound Preferences and select ALC883 Analog. I have the same trouble with the same driver (but luckily I have a second soundcard). First select it with ALSA. Play some music and test if the sound works. If that doesn't work, use OSS.

Josh :D

---

### Post by lake54 on 2009-06-05
Hey Josh,

I tried your suggestion in multiple variations, and sometimes it says Testing... (when I click the Test button, obviously) but no sound comes out, and others (I'd say 60-70% of the time) I get the following:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

Hope that helped somewhat.

James

---

### Post by propagation_of_sound on 2009-06-17
Are you using pulseaudio, alsa, oss?

---

### Post by propagation_of_sound on 2009-06-17
OK. If you've tried every alsa/oss, use pulseaudio:

sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter

Select PulseAudio in every case in Sound Preferences apart from Default Mixer tracks which will be the name of your soundcard

Then open up PulseAudio Device Chooser (padevchooser) and select your soundcard as the default sink and source and your host as the server.

And if that doesn't work, mess around in padevchooser until it works. 

Hopefully Audio will be fixed in Karmic fingers crossed.  

good luck.

---

