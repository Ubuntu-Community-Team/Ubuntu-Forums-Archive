---
title: "No Sound From New Build."
date: 2009-01-04
forum: Desktop Environments
---

### Post by SidTheKid on 2009-01-04
I have posted this on the "Absolute Beginners" Forum, but, the action there is so slow (three days, and, no response) that I thought I'd rephrase my situation on this forum.

I have just installed Ubuntu v. 8.10 on a desktop that is dedicated to Ubuntu (no freakin' Windows!!!) and can't figure out how to get the sound system to work. I've tried all the obvious things through System/Sounds, and, checked the settings via the speaker icon at the upper left of the screen (see, told ya I'm a newbie).

My sound card is an Audigy and is recognized as such (I think :oops:)

Everything else seems to be working properly. For example, my wireless network was instantly recognized and my video appears nominal, both with no input from me. Just blind luck.

If you can shed some light on this seemingly simply conundrum, I'd greatly appreciate your input.

Sid

---

### Post by cigtoxdoc on 2009-01-04
I had same problem under same circumstance.  I posted problem under multimedia.  Solution as posted there was to install gnome-alsamixer.

John

---

### Post by mali2297 on 2009-01-05
First check that no important sound channel is muted. You can do that with *gnome-alsamixer* or plain *alsamixer*. The latter is run in text-mode, just type
```

alsamixer

```
in a terminal.

If the above does not help, run the following commands in a terminal:
```

uname -a
aplay -l
lspci -v | grep -i -A5 audio

```
Post the output of each command. It will help us to troubleshoot.

---

### Post by SidTheKid on 2009-01-05
Mali, the result of the "uname -a" command is:

sid@sid-desktop:~$ uname -a
Linux sid-desktop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
sid@sid-desktop:~$ 
sid@sid-desktop:~$ 
sid@sid-desktop:~$ 
sid@sid-desktop:~$ aplay -1
aplay: invalid option -- '1'
Try `aplay --help' for more information.
sid@sid-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy [Audigy 1 [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy [Audigy 1 [Unknown]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy [Audigy 1 [Unknown]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The result of the "aplay -l" command is:

sid@sid-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy [Audigy 1 [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy [Audigy 1 [Unknown]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy [Audigy 1 [Unknown]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And, the result of the "lspci -v | grep -i -A5 audio" command is:

sid@sid-desktop:~$ lspci -v | grep -i -A5 audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Subsystem: Gateway 2000 Device 5288
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e400 [size=256]
	I/O ports at e080 [size=64]
	Memory at febff800 (32-bit, non-prefetchable) [size=512]
--
02:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
	Subsystem: Creative Labs Device 0058
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at dc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy

The result of the "alsamixer" command is:

 Card: PulseAudio                                                             &#9474;
&#9474; Chip: PulseAudio                                                             &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master                                                                 &#9474;
&#9474;                                                                              &#9474;
&#9474;                                     &#9484;&#9472;&#9472;&#9488;                                     &#9474;
&#9474;                                     &#9474;  &#9474;                                     &#9474;
&#9474;                                     &#9474;  &#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9500;&#9472;&#9472;&#9508;                                     &#9474;
&#9474;                                     &#9474;OO&#9474;                                     &#9474;
&#9474;                                     &#9492;&#9472;&#9472;&#9496;                                     &#9474;
&#9474;                                    81<>81                                    &#9474;
&#9474;                                  < Master >                               

Many thanks for taking a look at these values.

Sid

---

### Post by mali2297 on 2009-01-06
I see two sound cards listed in the output: Intel AC'97 and Creative SB Audigy. Does that seem right?

In alsamixer, the Master channel seems OK. But have you checked that PCM is not muted? (It should say 00 and not MM.) 

You could also experiment with the other channels. This (somewhat old) thread suggest that you should turn off "Audigy Analog/Digital Output Jack":
[http://ubuntuforums.org/showthread.php?t=407661](http://ubuntuforums.org/showthread.php?t=407661)

EDIT:
I see that you use pulseaudio. My advice might be outdated. I found a more recent post which contains a few links that might be useful:
[http://ubuntuforums.org/showpost.php?p=6502185&postcount=5](http://ubuntuforums.org/showpost.php?p=6502185&postcount=5)

---

### Post by SidTheKid on 2009-01-06
> **mali2297 said:**
> I see two sound cards listed in the output: Intel AC'97 and Creative SB Audigy. Does that seem right?

In alsamixer, the Master channel seems OK. But have you checked that PCM is not muted? (It should say 00 and not MM.) 

You could also experiment with the other channels. This (somewhat old) thread suggest that you should turn off "Audigy Analog/Digital Output Jack":
[http://ubuntuforums.org/showthread.php?t=407661](http://ubuntuforums.org/showthread.php?t=407661)

EDIT:
I see that you use pulseaudio. My advice might be outdated. I found a more recent post which contains a few links that might be useful:
[http://ubuntuforums.org/showpost.php?p=6502185&postcount=5](http://ubuntuforums.org/showpost.php?p=6502185&postcount=5)

Martin, I would guess that the Intel "sound card" is integrated into the Intel motherboard. The Audigy is a PCI card.

Is alsamixer the deal that opens when one double-clicks the speaker icon in the upper bar? In there, I unchecked the digital output jack option.

Still no sound. I'll look at your link. Many thanks for your able input. Here's a special treat, just for YOU, Martin:  :popcorn:

EDIT # 2: Martin, how can you tell that I use "pulseaudio"? I've never heard of this and it doesn't show up in the command listings. What the heck is pulseaudio?

---

### Post by mali2297 on 2009-01-06
> **SidTheKid said:**
> 
Is alsamixer the deal that opens when one double-clicks the speaker icon in the upper bar? In there, I unchecked the digital output jack option.

I think that's gnome-alsamixer, the result should be the same.

> 
EDIT # 2: Martin, how can you tell that I use "pulseaudio"? I've never heard of this and it doesn't show up in the command listings. What the heck is pulseaudio?

> **SidTheKid said:**
> 
The result of the "alsamixer" command is:

 Card: PulseAudio                                                             &#9474;
&#9474; Chip: PulseAudio                                                             &#9474;


I don't know much about pulseaudio, sorry. I need to update my knowledge about these audio things. :-(

---

### Post by SidTheKid on 2009-01-11
Still plodding away, trying to get sound out of this thing. Anyone else willing to weigh-in on this issue? Please! ):P

---

