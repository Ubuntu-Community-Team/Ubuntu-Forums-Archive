---
title: "Problems with microphone and Tapioca"
date: 2006-03-24
forum: Desktop Environments
---

### Post by jandi on 2006-03-24
Hi,

One of the things that keeps me booting back into windows is GoogleTalk.  Tapioca sounds like an awesome alternative now, however, I'm unable to get the microphone to work when using it.   It does work when using Skype.  
-
Sound device is Cirrus Logic CS4299.  Alsa Mixer says INTEL82801CA-1CH3.   My computer is an IBM A30 laptop.   In the Multimedia Systems Selector, the default sink is ESD (output) and default source input is OSS (I pretty much got to these by fiddling with them until the mic worked in Skype).

---

### Post by dudus on 2006-03-26
[quote=jandi]Hi,

One of the things that keeps me booting back into windows is GoogleTalk. Tapioca sounds like an awesome alternative now, however, I'm unable to get the microphone to work when using it. It does work when using Skype. 
-
Sound device is Cirrus Logic CS4299. Alsa Mixer says INTEL82801CA-1CH3. My computer is an IBM A30 laptop. In the Multimedia Systems Selector, the default sink is ESD (output) and default source input is OSS (I pretty much got to these by fiddling with them until the mic worked in Skype).[/quote]

Well I took some time till get my mic to work with tapioca.
This helped me:
[http://tapioca-voip.sourceforge.net/wiki/index.php/Configuring_Microphone](http://tapioca-voip.sourceforge.net/wiki/index.php/Configuring_Microphone)

---

### Post by jandi on 2006-03-27
Thanks.   What baffles me the most is that the microphone works correctly in Skype.  It took me a lot of fiddling with settings to get it to work in Skype in the first place, so I'm not sure whether any of these settings are conflicting with anything on Tapioca.   I have already tried the instructions on their site however, I still the mic is not working.  Also tried a second round of fiddling with the sink and sources to no avail   :(

---

### Post by dueyfinster on 2006-05-04
I still cannot get mine too work, even after using above links.
Card: Intel ICH6 
Chip: Analog Devices AD1980

Its all crackly for both reciever/caller. Any offers of help appreiciated!

---

### Post by akshaysrinivasan on 2006-05-04
My microphone too doesn't seem to work,but it was working in the beggining
chip:analog devices AC97

---

### Post by jandi on 2006-07-18
Mine is finally working.   I fiddled with so much stuff that I'm not sure what did it.   I disabled ESD

Also did
amixer sset capture cap


and made sure in multimedia devices ALSA was selected, and that microphone and capture were not muted.  I think.

---

### Post by raditzman on 2006-07-19
Hi, I've been trying to make skype work with my microphone using the same sound chipset (Cirrus Logic CS 4614/22/24) and I'm very happy to know that someone has made it work!!! I changed my settings as you said in the post (output to esd and input to OSS), however skype still isn't recording my voice. I was wondering how did you make so that skype ran through esd? Because it has the option to use alsa or OSS, which one did you choose?

---

### Post by spider-man on 2006-07-31
When I attempt to chat over Tapioca (Tapioca->Google Talk(Windows))the other person just hears crackling noises. They can't tell that it's my voice and they can't distinguish separate words. 

I've followed the instructions in previous posts to no avail. I have a Soundblaster Live 5.1 (emu10k1) with ESD running and my system is using ALSA. I can record crystal clear sounds with my microphone using arecord and Sound Recorder.

Does anyone have any ideas what could be causing these problems?

Thanks for your help

---

