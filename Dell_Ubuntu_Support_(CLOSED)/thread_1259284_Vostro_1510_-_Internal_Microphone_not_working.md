---
title: "Vostro 1510 - Internal Microphone not working"
date: 2009-09-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Wilbefast on 2009-09-06
I was just trying to get Skype to work on my Vostro 1510 under Ubuntu, but all I get when I speak into my laptop's microphone is white noise - the speakers work fine, as does the webcam, but I have no microphone: I tried voice recorder and I get the same distorted buzz whenever I speak. 

I've been trying to fix this myself using a few guides I've found on the internet, but so far all I've managed to do is cut off my sound completely by adding "options snd-hda-intel dell=DELL" to the end of "alsa-base.conf". I've reverted back to original but I'm pretty much out of ideas (and when I say ideas, I mean other people's ideas).

Does anyone know how I can fix this?

I have ALC268 - whatever the heck that means...


William

---

### Post by linux_tech on 2009-09-07
Check mic settings -
In a  terminal window
   Type  ```
 alsamixer
```
   
Select Capture (tab)
Right arrow to Capture, up arrow until its at a reasonable level ,
 right arrow to Input Source, up arrow to select Front Mic

---

### Post by Wilbefast on 2009-09-07
Fantastic!

Still very quiet though - I kept the two INPUT_SOs ones on MIC because if you change them to FRONT MIC I get a buzz. The two CAPTURs are on 81<>81 which is just into the red, but if I turn them much higher I get the buzz again.

Basically I fiddled around with alsamixer until the microphone worked, and then again till the popping sound that my speakers started making went away :P

Thanks very much for the help,

William

---

### Post by jmilamwalters on 2009-09-20
Though I have tried the aforementioned suggestions, among others provided on the internet, I am yet to make any progress with my Dell Vostro 1510 internal microphone using Ubuntu 9.10.  

In "Sound Preferences," within the "Devices" tab, under "Audio Conferencing," I attempt to test "Sound Capture" and receive the following message, regardless of the device I select:
[INDENT]gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback. Device is being used by another application.
[/INDENT]Ultimately, if possible, I intend to use the microphone for Skype.  Any suggestions on how I might approach this problem? 

Thanks!

---

### Post by Wilbefast on 2009-10-17
Erk - I just reinstalled and realised that I'd forgotten what the "magic" options were: I'm doing to put this here for future reference as it is probably the same story for other people too:

In [Capture]:
- Both inputs set to "Mic" to avoid the buzzing noise when recording (input)
- Right-hand CAPTUR set to 0 to avoid the popping sound when playing sound (not sure why sound capture would influence output but it does)
- Left-hand CAPTUR no higher than 81-81 or the recording will not work properly, no lower or the recording will not be audible except to Superman.
- Everything else should be able to go up to 100


Oh and jmilamwalters - didn't reply because I don't know how to solve your problem :( Any luck?


William

---

### Post by Pigi on 2009-11-08
I have a Dell Vostro 1510 with Ubuntu Karmic Koala: I solved the mic problem in this way:

- sudo gedit "/etc/modprobe.d/alsa-base.conf" 
- put a "#" at the start of the last line "options snd-hda-intel power_save=10 power_save_controller=N"
- save and reboot

after reboot check that input device on audio preferences is set on mic 1 (front mic) and on multimedia systems the default input is set on pulseaudio.

On alsamixer > Capture > Input So are set both on Mic, not Front Mic

In this way skype and front mic work both fine.

---

### Post by Wilbefast on 2009-11-09
I don't have 9.10 yet - going to upgrade at the same time as I upgrade to 64 bit...

BTW, an important note here - if you use Skype, make sure you turn OFF the option "let Skype automatically adjust your mixer settings" because if you don't it'll screw everything up each time you run it  :eek:


edit: I've upgraded to 9.10 - same settings seem to work here too so I didn't need to try Pigi's fix, not that there's anything wrong with I'm sure.

---

### Post by marn on 2009-12-30
Thanks for this post. Managed to get the internal mic on my vostro 1510 to work with the same settings as Wilbefast. 

Marn

---

### Post by tiosus on 2010-09-11
> **linux_tech said:**
> Check mic settings -
In a  terminal window
   Type  ```
 alsamixer
```Select Capture (tab)
Right arrow to Capture, up arrow until its at a reasonable level ,
 right arrow to Input Source, up arrow to select Front Mic
Fantastic

---

