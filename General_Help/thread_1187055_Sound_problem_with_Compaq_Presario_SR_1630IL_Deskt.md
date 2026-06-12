---
title: "Sound problem with Compaq Presario SR 1630IL Desktop"
date: 2009-06-14
forum: General Help
---

### Post by asamay81 on 2009-06-14
Hi,

i am very new to this forum. came with a problem. 

i am using Compaq Presario SR 1630IL desktop. before describing the problem with me, i would like to give the details of my system,

Intel Pentium 4, 3.06 GHz processor
Intel 915GV chipset
1 GB of RAM
MS-7174 motherboard, Manufacturar MSI, HP/Compaq motherboard name: Graphite-GL8E
Sound Card: Realtek ALC 880 chipset, High Definition Audio 

I have a dual booting (windows and ubuntu) system with ubuntu 9.4 as the default one.

Now the problem starts with me. 

In windows I do not have any problem with the sound, _but in ubuntu the sound is very less_. I have a Creative 2.1 channel speaker system with subwoofer. _If I put it to  the full volume then only i can listen the sound_. latter i have discussed with these guides:

```
http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html
```

```
http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html
```

_What happened is that after completing the installation and selecting everything to pulse audio sound server, i am being unable to open the *padevchooser *(the icon is there in Applications / Sounds & Video but is not launching). So i could not go forward and still in the trouble with the sound._

Checking *alsamixer* command in terminal shows everything 100%.

Keenly requesting everybody to help me in this regard so that I can get the sound from my PC in ubuntu.

With kind regards
Asamay

---

### Post by gradinaruvasile on 2009-06-14
Maybe this helps...

[http://ubuntuforums.org/showthread.php?p=7454288#post7454288]("http://ubuntuforums.org/showthread.php?p=7454288#post7454288")

My post there

And please post your links with the "insert link" method.

---

### Post by asamay81 on 2009-06-14
hi,

thanks for the reply. now the problem became more complicated. after removing the pulse audio there is no sound at all and terminal is also not recognising the *alsamixer* command. this error is coming
[FONT=Courier New]
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused
alsamixer: function snd_ctl_open failed for default: Connection refused[/FONT]

---

### Post by gradinaruvasile on 2009-06-14
What EXACTLY gives
alsamixer
in the terminal?

---

### Post by asamay81 on 2009-06-14
[FONT=Arial]this message:


ALSA lib pulse.c:272pulse_connect) PulseAudio: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused[/FONT]

---

### Post by asamay81 on 2009-06-14
Here are the full details what I have done with the Pulse Audio using these guides

[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

1. I have installed the packages described
2. Although Pulse Audio Device Chooser is not opening by clicking on it I could see "Pulse Audio Volume Control" in Applications/ Sounds and Video. Here is the volume control screen shot

[IMG]http://img291.imageshack.us/img291/2024/screenshotvolumecontrol.png[/IMG]

3. I have chosen the default sound card to PulseAudio from  System/Preferences/Default Sound Card

4. Here is the screen shot of System/Preferences/Sound where as mentioned I have changed everything to Pulse Audio Sound Server

[IMG]http://img29.imageshack.us/img29/1548/screenshotsoundpreferen.png[/IMG]

5. Now this is my panel volume control dialogue box

[IMG]http://img40.imageshack.us/img40/2871/screenshotvolumecontrolk.png[/IMG]

Everything i have followed whatever was written there. Although I am in dark with the sound - if I turn my speaker volume control to the full volume I can listen little sound. Help me please. Whether I have to use pulse audio or there is another solution for the same.

Thanks

---

### Post by gradinaruvasile on 2009-06-14
Read my link again. My post (#2)
 
The idea is to NOT use pulseaudio in fact disable it completely. And use ONLY alsa instead.
Like in the screenshot:
And all the other stuff is required to disable pulseaudio.

Edit and a bit off topic:

Pulseaudio is a sound server that works ON TOP of alsa, not something parallel. It causes trouble many times because it is not yet implemented to work seamlessly and painlessly. Pulseaudio may have all that fancy volume control and stream switcharoo stuff until its buggy and causes playback problems. ALSA in comparison has been in Linux for ages and is supported by virtually every program with sound playback/capture written for Linux. And is perfectly capable of playing back and recording from more than 1 source in the same time.

---

### Post by asamay81 on 2009-06-14
thanks gradinaruvasile. this is what i have followed you

1. I have chosen everything to ALSA
[IMG]http://img29.imageshack.us/img29/9588/screenshotsoundpreferene.png[/IMG]

2. kill pulseaudio has been added
[IMG]http://img200.imageshack.us/img200/1736/screenshotaddstartuppro.png[/IMG]

3. Default sound card has been set to "Intel" from "PulseAudio"

4. /etc/pulse/client.conf file has been edited and the other instruction has also been followed

5. Panel volume control dialogue box
[IMG]http://img231.imageshack.us/img231/2024/screenshotvolumecontrol.png[/IMG]

Now please tell me what is wrong with me. Still playback is less :(

---

### Post by asamay81 on 2009-06-15
somebody please help me.. switching on to ALSA also did not improve my sound condition..what should I do now? help me please.....

---

### Post by asamay81 on 2009-06-15
Today I have freshly installed Ubuntu 9.04 in my PC and here are the screenshots of the followings..I have installed these two after a fresh installation of Ubuntu

Alsa-mixer
Alsamixergui

1. alsa-mixer from terminal
[IMG]http://img95.imageshack.us/img95/6092/alsamixer.png[/IMG]

2. alsamixergui
[IMG]http://img141.imageshack.us/img141/3047/alsamixergui.png[/IMG]

3. gnomealsa-mixer
[IMG]http://img91.imageshack.us/img91/8340/gnomealsamixer.png[/IMG]

still the audio output is less from my external amplifier although it is in full volume. please tell me what is the wrong with me. is there any problem with the REALTEK ALC880 sound card in linux?

Thanks

---

### Post by asamay81 on 2009-06-16
nobody is reply me :( :(

---

