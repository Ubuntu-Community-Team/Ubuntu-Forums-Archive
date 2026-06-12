---
title: "[SOLVED] Can't get 5.1 surround sound to work"
date: 2007-08-01
forum: Dell  Ubuntu Support
---

### Post by mpospisil on 2007-08-01
I still haven't quite figured out how to get my 5.1 Logitech surround sound speaker system to work yet. If anyone can help me with this I would appreciate it. The two front speakers, the sub, and the middle speaker work, but the other two back speakers don't work yet.

---

### Post by mpospisil on 2007-08-03
So no one knows how to get surround sound working or is it just something really simple that I can't figure out?  I tried changing my .asoundrc file so that the back speakers mimick the front ones but thats not working either.

---

### Post by strabes on 2007-08-03
It's probably a problem with the support of your sound card, not your speakers.

I have the logitech Z-5500 speakers which has Dolby Pro Logic II. This feature takes stereo tracks that I run through the standard analog port on my laptop and pipes it through all six speakers.

---

### Post by mpospisil on 2007-08-03
Yeah I figured that it was a problem with my sound card.  I have a 7.1 capable sound card that I believe is integrated.  I tried installing an external creative live! 24 bit sound card through usb and that one does the same thing.  Does anyone know how I can get the sound card to work with Linux so I can fully utilize all my speakers?

---

### Post by mgmiller on 2007-08-03
To turn on surround sound:
1) Open the volume control by double clicking the speaker icon in the top panel.
2) Click on edit preferences.
3) Put check marks in both the surround and channel mode boxes.
(you will have to scroll down the list to find channel mode)
4) Make sure the slider for surround is turned up and not muted.
5) On the Options tab, select 4ch, 6ch or 8ch as appropriate. 

:guitar:
To test the speaker set up with a spoken voice for each speaker,
copy the following commands to a terminal.

7.1 channel surround:
speaker-test -Dplug:surround71 -c8 -l1 -twav 

5.1 channel surround:
speaker-test -Dplug:surround51 -c6 -l1 -twav

4 channel surround:
 speaker-test -Dplug:surround40 -c4 -l1 -twav

2 channel:
 speaker-test -Dplug:front -c2 - l1 -twav

the -l1 makes it play the voice 1 time, change the number to anything reasonable.  If you leave this out it repeats till you close the terminal..

for more info  man speaker-test

Note:
Sometimes you may have to move the actual speaker jacks around while the voice is describing which channel is which to get everything right.

---

### Post by chuck_h1987 on 2007-08-03
I have a Panasonic 5.1 Surround for mine. It works fine. What snd card r u running?

---

### Post by JerMe on 2007-08-05
> **mgmiller said:**
> To turn on surround sound:
1) Open the volume control by double clicking the speaker icon in the top panel.
2) Click on edit preferences.
3) Put check marks in both the surround and channel mode boxes.
(you will have to scroll down the list to find channel mode)
4) Make sure the slider for surround is turned up and not muted.
5) On the Options tab, select 4ch, 6ch or 8ch as appropriate. 

:guitar:
To test the speaker set up with a spoken voice for each speaker,
copy the following commands to a terminal.

7.1 channel surround:
speaker-test -Dplug:surround71 -c8 -l1 -twav 

5.1 channel surround:
speaker-test -Dplug:surround51 -c6 -l1 -twav

4 channel surround:
 speaker-test -Dplug:surround40 -c4 -l1 -twav

2 channel:
 speaker-test -Dplug:front -c2 - l1 -twav

the -l1 makes it play the voice 1 time, change the number to anything reasonable.  If you leave this out it repeats till you close the terminal..

for more info  man speaker-test

Note:
Sometimes you may have to move the actual speaker jacks around while the voice is describing which channel is which to get everything right.

Well written response.  Thanks!

---

### Post by mpospisil on 2007-08-06
First of all when I opened the sound control for my HDA Intel Alsa Mixer there wasn't a channel mode, but there was a surround sound mode to check.  In the options tab there wasn't a 4ch, 6ch, 8ch to select. 

 I did run the 6 channel speaker test and my front two speakers are correct.  However, the rear right came out of the subwoofer and rear left came out of the center speaker.  The center test came up blank.   I have all the cables hooked up correctly because I have checked many times.

 Is there a way that I can re-route the sound to come out which speaker?

This is my card.  It's just an integrated Intel 7.1 sound card.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by mgmiller on 2007-08-07
> In the options tab there wasn't a 4ch, 6ch, 8ch to select.
Every rear channel capable card I have tried this with has had a small drop down box in the options tab, to select the number of speakers, once the surround box was checked.

> I did run the 6 channel speaker test and my front two speakers are correct. However, the rear right came out of the subwoofer and rear left came out of the center speaker. The center test came up blank. I have all the cables hooked up correctly because I have checked many times.

Just because you have them plugged into what are at first labeled the "correct" ports, doesn't mean they will work that way.  Many modern integrated sound systems auto detect the cables and change the sound outputs around.  The only way around this that I have used reliably, is to play the sounds that identify which speaker is which and plug them into the corresponding ports, regardless of what the label on the port or in the mobo manual says.  I have also found that sometimes I get better quality sound out of different ports for the front speakers.  More than one set may correctly produce front right and front left, but with different quality.  The only way to know is to try the plugs in all the available jacks till the speaker test correctly identifies each one.

Good Luck.

---

### Post by mpospisil on 2007-08-07
My problem was that I had the January version of the Alsa driver, lib, and util.  I simply downloaded all three from the Alsa website and recompiled them with my sound card hda-intel.  My particular card has a chipset of SigmaTel STAC 9227.  After figuring out a couple small errors, I ran the test speaker-test -Dplug:surround51 -c6 -l1 -twav and now all my speakers work correctly without unplugging, re-routing, or reconfiguring any cords.  Thanks to all those who tried to help.

---

### Post by pappfer on 2007-12-11
I have an Acer Extensa 5620 notebook, a Genius 5.1 surround speaker system and running Gutsy. I had the problem that I couldn't get any sound from the external speakers at all. After I installed linux-backports-modules I can get sound from front left and front right speakers but none of the others.

In the options tab I don't even have the "Surround" checkbox at all. I tried some of the methods written here, but the best I could get is to get sound from only 2 speakers: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

What else could I try to make 5.1 surround sound work?

---

### Post by agamum on 2007-12-28
> **mgmiller said:**
> To turn on surround sound:
1) Open the volume control by double clicking the speaker icon in the top panel.
2) Click on edit preferences.
3) Put check marks in both the surround and channel mode boxes.
(you will have to scroll down the list to find channel mode)
4) Make sure the slider for surround is turned up and not muted.
5) On the Options tab, select 4ch, 6ch or 8ch as appropriate. 

:guitar:
To test the speaker set up with a spoken voice for each speaker,
copy the following commands to a terminal.

4 channel surround:
 speaker-test -Dplug:surround40 -c4 -l1 -twav


I have done these instructions on my machine.

**In the speaker test all is fine, I hear the voice in EVERY speaker wihout any problem.**

But when playing sounds (i.e. a mp3 file or something else) I **only hear sound in 3 speakers, I miss the left front** without apparently any reason for this.

**In 2ch mode the front left speaker is working right too**, all the problem is when going to 4ch, but only for applications, the test command is ok too! :(

Please can someone help me?.

This is my audio specs:

Integrated audio of mainboard ASUS M2NPV-VM, chipset SoundMax ADI AD1886A.

PS. I'm new to linux world, trying to switching from windows to ubuntu. So please, be helpful with me :)

---

### Post by allanandr3w on 2008-03-02
> **mgmiller said:**
> To turn on surround sound:
1) Open the volume control by double clicking the speaker icon in the top panel.
2) Click on edit preferences.
3) Put check marks in both the surround and channel mode boxes.
(you will have to scroll down the list to find channel mode)
4) Make sure the slider for surround is turned up and not muted.
5) On the Options tab, select 4ch, 6ch or 8ch as appropriate. 

:guitar:
To test the speaker set up with a spoken voice for each speaker,
copy the following commands to a terminal.

7.1 channel surround:
speaker-test -Dplug:surround71 -c8 -l1 -twav 

5.1 channel surround:
speaker-test -Dplug:surround51 -c6 -l1 -twav

4 channel surround:
 speaker-test -Dplug:surround40 -c4 -l1 -twav

2 channel:
 speaker-test -Dplug:front -c2 - l1 -twav

the -l1 makes it play the voice 1 time, change the number to anything reasonable.  If you leave this out it repeats till you close the terminal..

for more info  man speaker-test

Note:
Sometimes you may have to move the actual speaker jacks around while the voice is describing which channel is which to get everything right.


followed all your instruction, but i have to check "duplicate front" and my center speaker does not work, my motherboard is P4P800-e deluxe with built in surround sound. that this mean my 5.1 channel is not configured properly?

---

### Post by mgmiller on 2008-03-04
A few things you can try for this mobo.
1) make sure the BIOS is configured correctly for the number of speakers you have.

2) make sure the jumper on the mobo for sound is set correctly.  Look behind pci slot number 4 (second from bottom) If it is removed, the back panel audio jacks won't work right.

3) are you sure all the wires are correctly plugged in on the back of the mobo? I think the lime colored wire is supposed to be center channel.

4) are the volume controls on the speakers themselves turned up for center channel? 

5) try running alsa mixer in a terminal:
```
alsamixer
```

Use the right and left arrow keys to go to the entry for the center channel.  
Use the up and down arrow keys to set its volume.  Make sure it is not muted by looking at the bottom of the volume column.  It should say 00.  If it says MM it is muted.  

Use the letter m key on the keyboard to toggle mute off and on.


I am assuming you have a 5.1 speaker setup.  Does the output of 
```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```
give you  correct response?

---

