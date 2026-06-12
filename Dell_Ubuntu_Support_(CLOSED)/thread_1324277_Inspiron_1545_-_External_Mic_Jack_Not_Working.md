---
title: "Inspiron 1545 - External Mic Jack Not Working"
date: 2009-11-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by stephen.d.francis on 2009-11-12
I've recently installed Ubuntu 9.10 (Karmic Koala) onto my Dell Inspiron 1545 (CD install from ISO, rather than Wubi), and have got nearly everything working nicely, except for my external mic which I plug into the 3.5mm jack at the front of the machine, and which refuses to work despite all my efforts.

All other sound configuration seems working fine, including the built-in mic, and playback through headphones and speakers.

I've followed the advice from several threads, including:
- opening Sound Preferences and checking all settings:
   - Hardware tab, device profile = Analog Stereo Duplex
   - Input tab, mute is unchecked
- uninstalling and then re-installing ALSA and various other components
- installing GNOME Alsamixer

In doing all this, I've never seen anything that seems to correspond to the external mic as opposed to the built-in one. E.g. in Sound Preferences, Input tab, there are two "Connectors" - "Microphone 1" and "Microphone 2", but both seem to relate to the built-in mic - there's no other option there that I would expect for another device - the mic jack.

I have seen references to "Mic Jack Mode" in ALSAMixer - but checking the box seemed to have no effect.

It seems to be quite a low-level issue - that the PC has a hardware component that Ubuntu has not picked up on at all; or else that the external mic feed is supposed to come through the same sound card, but isn't for some reason.

I am at the limit of my knowledge, and any help or advice would be most welcome. Thanks.....

---

### Post by mikewhatever on 2009-11-12
In my case, there is a switch in alsamixer for internal and external mic. I use the terminal version, so if I type 'alsamixer', and then hit Tab once or twice to cycle through the switches, I get the picture below, and rightmost is the mic switch. Move to the desired switch with left and right arows, and toggle the options with up and down ones.

---

### Post by stephen.d.francis on 2009-11-21
I'm afraid that doesn't help for me :(, but thanks for the suggestion...

---

### Post by gregorvm on 2010-01-17
I have the had the  problem on my dell studioXPS , no mic/line input , whatever i do. I found on other fora (also on dell community) the same problem but no solution. A minute ago i found out that the solution for me was changing the DIGITAL input source to Analog input in Alsamixer .
Thanx for the help

---

### Post by chill3570 on 2010-02-26
This worked for me also. changed to inline and digital to mono using that command line utlity.

---

