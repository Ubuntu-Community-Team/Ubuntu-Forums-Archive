---
title: "Audio playback stopped working on 8.10"
date: 2009-01-17
forum: General Help
---

### Post by Taidgh on 2009-01-17
Up until recently, my sound has worked fine (out of the box). I bought a Samson Q1U usb mic today, and got that working well on my laptop (8.10). When I unplugged it sound playback was no longer working. When I try to test 'SiS S17012 with ALC200,200P SiS 717012 (ALSA)' in sound preferences, I get ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
``` Autodetect just leaves me with a 'Testing...' message and no sound. Here is my lspci, if it is relevant:
```
taidgh@ephedra:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

```

---

### Post by Taidgh on 2009-01-18
I get the same message:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```
when I try to use my soundcard (SiS SI7012) with OSS. A problem with drivers?

---

### Post by Taidgh on 2009-01-18
Do not try to bump the thread. Instead try to realise the truth. What truth? That there is no thread.

---

### Post by Taidgh on 2009-01-18
```
#!/usr/bin/env python
import bump
for bump in bump:
    print "Bump."
    bump+=1
```

---

### Post by mssever on 2009-01-18
Have you seen this thread? [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I'm guessing your problem has something to do with PulseAudio, though I don't know enough about pulse to be able to help you with it.

---

### Post by Taidgh on 2009-01-18
I tried following the guide and it didn't work. If I get no sound at all (no startup or login sounds) would it still be related to PulseAudio? Also, system_1 and system_2 no longer show up as readable output ports in Jack.

---

### Post by Taidgh on 2009-01-19
Right, I guess I'm reinstalling again. I'm begining to tire of Ubuntu...

---

