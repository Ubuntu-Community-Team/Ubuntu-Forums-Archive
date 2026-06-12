---
title: "No sound, but I do have two options. Which one?"
date: 2006-08-08
forum: Desktop Environments
---

### Post by UltraSonicSite on 2006-08-08
When I open the sound preferences window I have two options, well sort of. The first 

SB Live 5.1 [SB0220]

The second

C-Media PCI [some numbers]

The first one yields no sound, while the second one, for whatever reason is not activated when told to. Opening up the Sound Preferences window again just shows SB Live 5.1 again.

How do I get sound?

---

### Post by computergroove on 2006-08-08
First, do you have onboard sound? If you do I would take out the sound blaster and just use the cmedia sound card. If you are determined to use the soundblaster card you will need to go into the cmos setup (assumung that its an onboard card) and disable it. Installing sound cards in linux is very hard. There should be drivers ready for the cmedia card.

---

### Post by UltraSonicSite on 2006-08-09
How do I enter this so called, Cmos Setup?

---

### Post by UltraSonicSite on 2006-08-09
Anyone know?

---

### Post by GoLoGo on 2006-08-09
Press Del usually before your computer displays anything when you start your computer. Other computers usually Toshibas, Dells, Gateways, its F2 - Usually it tells you what to press. Sometimes its F8 - your cmos is your bios, usually its one of those keys, try em all. See which one takes you into your "setup configuration" screen.

---

### Post by mg3kc on 2006-08-09
> **UltraSonicSite said:**
> How do I enter this so called, Cmos Setup?

I think they mean its a BIOS option... press the Del. key as the computer is starting up and try to find the disable onboard sound option.

---

### Post by UltraSonicSite on 2006-08-09
Oh I get it, I usually don't go in there.

---

### Post by UltraSonicSite on 2006-08-09
I dont think whatever I changed did anything at all. The odd thing is that sound had worked before the big kernel update. Now I get no sound? Any information you guys need to help me?

Edit: Whatever I changed actually disabled the C-Medidia and now I only can choose my soundblaster card.

---

### Post by UltraSonicSite on 2006-08-09
> **computergroove said:**
>  should be drivers ready for the cmedia card.

For some reason I can't select the Cmedia card.

---

### Post by mg3kc on 2006-08-09
> **UltraSonicSite said:**
> I dont think whatever I changed did anything at all. The odd thing is that sound had worked before the big kernel update. Now I get no sound? Any information you guys need to help me?

Edit: Whatever I changed actually disabled the C-Medidia and now I only can choose my soundblaster card.

If you were a windows user I would ask whether or not you had the speakers turned on!

Oddly enough, my sound also had some issues with the kernel update, but when I fiddled around a bit I got back to where I was. 

Any error messages would help...

---

### Post by UltraSonicSite on 2006-08-09
[IMG]http://img.photobucket.com/albums/v64/ultrasonicsite/Screenshot.jpg[/IMG]
When I hit close it reverts back to the Sound Blaster option

---

### Post by mg3kc on 2006-08-09
When you press on one of the play buttons for login/logout does anything happen (error messages?)
What about when the SB card is selected?

---

### Post by christhemonkey on 2006-08-09
If you want your Cmedia card to be the default option:
Type into a terminal:
```
aplay -l 
```
This lists all the sound devices registered with ALSA (the sound thing:)).

Then it should have lots of things about devices and subdevices.
Basically your Cmedia will be one of the main devices (with subdevices like DA converter listed underneath).
Remember what device number it is (probably 1)
Then type:
```
sudo alsactl store 1 
```
Obviously replacing 1 with the actual number (which should be either 0 or 1)
This stores your selection for default soundcard (like the dialog box does, but actually works :p)

Hopefully, if your speakers are plugged into your Cmedia card, you should be able to hear sounds play now!

```
aplay /path/to/a/wave/file.wav 
```
Will give you a definitive test.
It should playback a wav file (if you give it the path and name of a real wave file!)

---

### Post by UltraSonicSite on 2006-08-09
> ultrasonicsite@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SB Live 5.1 [SB0220]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Live [SB Live 5.1 [SB0220]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SB Live 5.1 [SB0220]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ultrasonicsite@ubuntu:~$ sudo alsactl store 1

Still has soundblaster selected on the sound menu, and still no sound. Is it odd that there are more than one 0's and 1's?

---

### Post by christhemonkey on 2006-08-09
I tend to ignore the sound menu, it never has worked right for me :)
If aplay will play something, then all the things using alsa will work.

Even if a silly help option says it wont :p

I have found that if i open that sound menu, i may need to rerun those commands:
```
sudo alsactl store 1 
```
And then test with aplay:
```
aplay /whatever/file.wav 
```


EDIT: Oh and having lots of subdevices for a soundblaster compared to a C-media is not so odd (i dont think?)

---

### Post by UltraSonicSite on 2006-08-09
Did I forget to mention my computer is connected to a dolby 5.1 Surround Sound Prologic home entertainment system? My regular speakers don't work o.o

---

### Post by UltraSonicSite on 2006-08-09
> ultrasonicsite@ubuntu:~$ aplay /home/ultrasonicsite/Shared/Tunnel* Playing raw data '/home/ultrasonicsite/Shared/Tunnel Trance Force 2001 - dhs - h ouse of god (best techno song ever).mp3' : Unsigned 8 bit, Rate 8000 Hz, Mono
I'll try changing where the cable is connected while it plays.

---

### Post by christhemonkey on 2006-08-09
I imagine you would be wanting to use your soundblaster 5.1 card then?!
```
sudo alsactl store 0 
```

That should use that soundcard as default,
then checking everything is on and connected,
do the whole aplay a wav file.

---

### Post by UltraSonicSite on 2006-08-09
Success!!! I started hearing some interference while it was playing from the Terminal. I switched to movie player, and soooound.  =D 

See I have two seperate locations on the back of my computer, I guess one is for the SoundBlaster and the other for CMedia.

---

### Post by UltraSonicSite on 2006-08-09
> **christhemonkey said:**
> I imagine you would be wanting to use your soundblaster 5.1 card then?!
```
sudo alsactl store 0 
```

That should use that soundcard as default,
then checking everything is on and connected,
do the whole aplay a wav file.

My computer is wierd like that, Cmedia pwns SoundBlaster on linux I guess.

---

### Post by christhemonkey on 2006-08-09
Congratulations!
Is this using the C-media or the SBlive 5.1?

---

### Post by UltraSonicSite on 2006-08-09
> **christhemonkey said:**
> Congratulations!
Is this using the C-media or the SBlive 5.1?

C-Media

---

### Post by christhemonkey on 2006-08-09
I have one of those! (Cmedia)
its about 11 years old now...
Sound blaster live 5.1 should work fine!

From [here]("http://ubuntustudio.com/wiki/index.php/Audio_Hardware#Creative_SoundBlaster_Live.21_5.1_Sound_Card"):
>  Creative SoundBlaster Live! 5.1 Sound Card
This card worked great under Linux!


---

### Post by UltraSonicSite on 2006-08-09
> **christhemonkey said:**
> I have one of those! (Cmedia)
its about 11 years old now...
Sound blaster live 5.1 should work fine!

From [here]("http://ubuntustudio.com/wiki/index.php/Audio_Hardware#Creative_SoundBlaster_Live.21_5.1_Sound_Card"):

Actually it might be SB 5.1 thats on, atleast thats what the sound menu still says lol

---

### Post by christhemonkey on 2006-08-10
The real question being whether you have 5.1 surround sound?

---

