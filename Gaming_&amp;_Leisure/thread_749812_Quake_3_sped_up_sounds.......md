---
title: "Quake 3 sped up sounds......"
date: 2008-04-08
forum: Gaming &amp; Leisure
---

### Post by k5dreadlord on 2008-04-08
Hey there everybody, I'm kind of new to Linux and am having a problem with my sound.

The sound in quake 3 looks like it's been sped up a lot, the pitch is also altered, like chipmunk voices...

I read somewhere on an apple forum that it had to do with the sample rate of my sound card being at 48000, I changed it through alsamixer, my emu 1820 now shows 44.1 but the problem persists. I even tried changing the sample rate in qjackctl, even though jack sever won't even start... Oh and for some reason I can't change the resolution in Quake 3 either, I tried 1024x768 instead of the default 640x480 and the game just quit.

I noticed Starcraft also does this (The sound problem), I'm currently running this game through Wine.

Thanks a bunch in advance
FX

---

### Post by Crafty Kisses on 2008-04-08
What are your system specs? Also post the following output:
```
lspci
```

---

### Post by k5dreadlord on 2008-04-08
Specs added to my signature!

Sorry for asking but what exactly are you asking me to post? 

I'm a new user you know...

---

### Post by Crafty Kisses on 2008-04-08
> **k5dreadlord said:**
> Specs added to my signature!

Sorry for asking but what exactly are you asking me to post? 

I'm a new user you know...

It gives me info about your soundcard, also are you running desktop effects when this occurs?

---

### Post by k5dreadlord on 2008-04-08
Doh! No wonder I couldn't get lspci to work, I forgot to su - beforehand...
Anyways I'll post it now. I don't use desktop effects, at least as far as I know, a friend mentionned it before but I never installed the thing.

[PHP]00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:0b.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 01)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
[/PHP]

---

### Post by Crafty Kisses on 2008-04-08
Are you running Ubuntu or openSUSE?

---

### Post by k5dreadlord on 2008-04-08
OpenSUSE 10.3

Wish I had a squirrell in my name... Looks neat!

---

### Post by Crafty Kisses on 2008-04-09
> **k5dreadlord said:**
> OpenSUSE 10.3

Wish I had a squirrell in my name... Looks neat!

Haha, thanks! Do you have desktop effects enabled when this occurs?

---

### Post by disturbedite on 2008-04-09
this isn't directly relevant to your sound problem, but i actually recommend that people don't use official q3 for linux.  please see my post here:
*[http://ubuntuforums.org/showthread.php?p=4637809#post4637809](http://ubuntuforums.org/showthread.php?p=4637809#post4637809)*

---

### Post by k5dreadlord on 2008-04-09
I don't think I ever installed desktop effects. If it's in OpenSUSE by default I don't remember activating it either.

I'll check out that guy's thread and see if it helps! Thing is it happens in Starcraft and in some videos using Kaffeine also (I'll check wich video formats specifically do this) so it's only going to be a fix to Q3 at best...

---

### Post by disturbedite on 2008-04-10
well, if its effecting these multiple things, then it seems more likely that its a driver problem.

---

### Post by k5dreadlord on 2008-04-11
I'll just roll back my alsa drivers one version and see what it does. Stay tuned for results!

---

### Post by k5dreadlord on 2008-04-11
Rolled back my alsa driver, didn't work.
Wonder if it's a decoder config problem, suggestions anyone?

---

### Post by k5dreadlord on 2008-04-12
Update: The intro movie in Starcraft Broodwar is in fast forward, both audio and video in this case, the game runs at normal speed though.
The intro to Quake 3 doesn't have any sound at all.

Both games run at the right speed except for audio during gameplay.

Does anyone know how to tweak the options in xine, wine and the engine running the audio for Quake 3, when I go to winecfg it says it can't find the alsa driver and if I click on the Control Panel button, it says it's not implemented yet...

Any help would be appreciated, I believe it might be a problem with the xine engine being set to 48000, and I don't know how to change it.

---

### Post by disturbedite on 2008-04-12
as far as the SCBW intro is concerned...
i think, and i could be wrong, i remember reading that there are known issues with the playback of blizzard videos.  so that may not be an issue caused by your system/setup.

---

### Post by k5dreadlord on 2008-04-13
Hmm interesting, I'll go and check that out. I'm troubleshooting Starcraft instead of Quake, wine being easier to tweak.

Still working on my sound issue, I reinstalled wine and now the damn thing tells me it can't find my alsa drivers and removed it from the registry!
Also the wine Control Panel in the audio options doesn't start, it says it's not implemented yet...

---

