---
title: "MIDI FAQ/how to?"
date: 2006-04-27
forum: Desktop Environments
---

### Post by entryname on 2006-04-27
Hi gang

At the risk of everyone groaning "not that AGAIN", I'm very unsure about MIDI on Ubuntu. I was never aware of a sound problem running Windows 98 on this machine. Device manager reports that I have YMF724 and blathers on about Yamaha DS-XG PCI, AC'97, PCI and ALSA devices. I don't know if this means its supposed to do MIDI or not.

I tried Rosegarden2 but that seems to think it hasn't got anything to play MIDIs on and referred me to this:

michael@ubuntu:~$ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux ubuntu 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Yamaha DS-XG (YMF724) at 0xec000000, irq 10

Audio devices:
0: YMFPCI (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: SigmaTel STAC9704

This is still how it reads after installing timidity.

Where is this config that it's on about? is it not enabled because it needs twiddling, or because when Ubuntu originally installed it decided my system couldn't do it?

I gather MIDI is a hardware standard tho it can be circumvented by software synthesisers. So the $64,000 question is, suppose I want Rosegarden to at least believe it has something to play back on, and get some sound out of it. How do I do it??

Sorry if this sounds a stupid question :confused:

---

### Post by Stinger on 2006-04-27
I might be able to help you.
I got midi playback working using the instructions on the wiki.
[MidiSoftwareSynthesisHowTo]("https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo")
BTW. I have a Terratec Aureon card using the snd-ice1724 alsa driver.
When you get to the soundfont part please try the Unison.sf2 soundfont it's really good.
Hope it helps.:-D

---

