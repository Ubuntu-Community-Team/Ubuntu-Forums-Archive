---
title: "No sound in Applications, works fine in Totem."
date: 2009-05-20
forum: General Help
---

### Post by Serpher on 2009-05-20
I just upgraded to 9.04 and I can get everything to work except in applications such as aMSN, Firefox, or in any kind of game, I get no sound. I can listen to music and watch movies in Totem, but nothing else. All of my sound settings are set to OSS as ALSA will not work unless I change the output device with ALSA and that doesn't fly with anything but Sound Playback...help?

---

### Post by Serpher on 2009-05-21
Here's what I get when I type lspci

```
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub (rev c0)
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port (rev c0)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Network controller: RaLink RT2800 802.11n PCI
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
06:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
```


My onboard sound is:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


[[IMG]http://img520.imageshack.us/img520/9738/screenshothhb.png[/IMG]](http://img520.imageshack.us/my.php?image=screenshothhb.png)


If anybody has any idea even where to begin looking it would be much apprichiated.

---

### Post by clhsharky on 2009-05-21
OSS is old, in Jaunty I use ALSA and PulseAudio on all my computers. All so check in Multimedia and Video section 
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)
a search ther should help.

---

### Post by SonicSteve on 2009-05-22
Try this,

Right click the sound icon in up by the clock. 
Choose open volume control
First play with all the different options under Device
Second as your playing be sure to click the preferences button at the bottom of each device. Make sure each configuration option has a check mark. Then make sure something isn't muted or set too low. 
Sometimes even adjusting the volume of each option will jog it back to life.

Back in the days of 6.06 the sound would sometimes mute all by itself, I would fix it by doing what I listed above.

---

### Post by Serpher on 2009-05-23
I checked out the sound options and I still get no sound. Also when I test my sound under ALSA or Pulseaudio I get

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.

---

