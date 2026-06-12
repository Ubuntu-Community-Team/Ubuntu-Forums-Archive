---
title: "Sound issues (zsnes, pSX, wine)"
date: 2008-05-09
forum: Gaming &amp; Leisure
---

### Post by nunix on 2008-05-09
NOTE: NOT JUST A WINE PROBLEM (I did see the sticky ;)

This is under 7.04 on a HP Pavilion laptop; the sound chip is something onboard, SoundMAX something (don't remember exactly what, haven't used XP for quite awhile now and am not sure how to dig up the device info in ubuntu)

The problem is: super-scratchy sound, and terminal error messages all regarding underruns.

zsnes 1.51 (downloaded and compiled, not apt-get or synaptic) spits out the following:

Starting Mouse detection.
Unable to poll /dev/input/event10. Make sure you have read permissions to it.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: Simple DirectMedia Layer output
Channels: 2
Rate: 32000

pSX 1.13 spits out, every couple of seconds:

sound: underrun
sound: underrun
sound: underrun
(etc)

wine (not sure what version it is, installed via apt-get I think) spits out tonnes of:
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=5564 < primary_done=24384)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=5564 < primary_done=24384)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=5564 < primary_done=24384)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=5564 < primary_done=24384)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=5564 < primary_done=24384)

...and on exiting throws out a few pages of stuff that looks like a generic error report that's barfing out everything. 

Now, it seems like all of this must have a common origin, because the sound issue is EXACTLY the same under all these programs. 

I can play MP3s fine (but no midis, haven't figured out what I need to do there yet) and watch video. The only trouble comes when running these programs for games. 

I've dug around on the boards and google but have not come up with exactly the same problem that others have, so I've been pretty uncomfortable making changes to config files that I don't understand just cos it's kinda-sorta-similar. ;)

Any help would be reaaaally appreciated.. I turned off sound in Dwarf Fortress for a long time to deal with the wine problem, but would like the sound for zsnes and pSX. =p

---

### Post by dfreer on 2008-05-09
Hmmm, I have a HP Pavillion dv6000t, can't remember my sound card either. Anyways, zsnes sound generally works best if you use zsnes 1.51 with OSS (run zsnes once with -ad oss), using a build with libao enabled (--enable-libao when compiling). 

If you'd rather not do that, you can install libsdl1.2debian-oss (restart is probably a good idea), which should increase sound quality to very near perfect (assuming this is a problem with zsnes and not your sound card).

pSX I've always increased the latencies by 10 ms to reduce crackling and the such.

---

### Post by acoustibop on 2008-05-09
As dfreer suggests, these are probably two different issues.  pSX seems to require fairly low sound latency, and since this tends to be higher in Linux distributions (although Gutsy and now Hardy are getting better and better) than in Windows, it's a problem that crops up more in Linux.  Messages saying that you have sound underruns are a symptom of this.  Sound latency can vary quite a lot between different soundcards and many onboard chips seem to be particular offenders in this respect.  Also as dfreer says, the best way to deal with it in pSX is to increase the values for the Latency sliders on the Sound tab in Configuration; however, don't overdo it, as the Latency sliders in pSX are essentially introducing a delay - too much and you'll find your sound going out of sync.

Apart from your onboard sound chip being a probable contributer to this, nunix, and one that you probably can't change, you could try upgrading to Hardy: sound latency is already much improved over previous releases in Gutsy, and Hardy is even better.

As far as ZSES is concerned, the problem can be a little complex in that different sound drivers seem to work best from system to system. I've found for a while now that, for other games and applications as well as ZSNES, it can be a good idea to install libsdl1.2debian-all to give you a wider choice of drivers (don't worry if it removes libsdl1.2debian-alsa, support for the ALSA driver will be restored in libsdl1.2debian-all).  Check that you have libao2 installed, as well; I can't remember if it is by default in Feisty.

Now that you have a wider range of drivers to choose from, open a terminal and enter 'zsnes --help' - omitting the quotes, of course.  This will give you a list of driver options for ZSNES.  Note them down and try each one with 'zsnes -ad "driver option"' where "driver option" is the one you want to try.  When you've found which one works the best, do 'zsnes -ad "driver option"' again with that one, and that will configure ZSNES to use it in future.

Incidentally, Gutsy and Hardy both have the current ZSNES version 1.51 in their repositories, rather than version 1.42 (AIR) that's in the Feisty ones.

---

### Post by nunix on 2008-05-09
Thanks, I'll give these a shot.

Upgrading isn't really an option, unfortunately; my optical drive has given up the ghost at this point, and this BIOS can't boot from USB. I'd originally tried to install Gutsy but there was some bizarre hardware incompatibility because I could not boot a Gusty live or alt CD, but could boot a Feisty.. even though both discs worked in desktop PCs (so I know the discs were good). I'd read other HP/laptop issues with Gutsy when it came out, and I don't want to just do a download-upgrade, would prefer a clean one. 

Anyway! 'ppreciate the tips, will give these a shot and see what happens.

---

### Post by acoustibop on 2008-05-09
AIR I had a problem booting a Gutsy CD/DVD and now with Hardy, nunix, in that there's no display when it boots; this is easily fixed by booting in Safe graphics mode, however.  This problem didn't occur in Feisty.

Laptop optical drives don't seem to last that well; but I'd say that, if this is going to continue to be your working machine, it would be well worth while investing in another one.  apart from anything else, it must be pretty inconvenient running a Playstation emulator without one! ;)

---

