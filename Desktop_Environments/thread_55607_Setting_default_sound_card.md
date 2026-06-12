---
title: "Setting default sound card?"
date: 2005-08-09
forum: Desktop Environments
---

### Post by Thresher on 2005-08-09
I have a feeling this may be answered *somewhere* in the forums, but I've been looking for days with no luck, so here goes:

I have a motherboard with onboard sound, and a soundblaster live soundcard. I want to use my Soundblaster card, but the sound always goes to the onboard sound.

I know that kubuntu can use the card because the first time ran Kaffeine the sound came through my sound card. I may have done something after that because Kaffeine stopped playing through my soundcard, but I got it to do it again for a while by just messing around with the basic xine settings once.

I just want to have all my sound come through my Soundblaster card instead of the onbard, but so far I haven't figured out how to do that.I'd love any help, tips, or links anyone can provide.

---

### Post by gingermark on 2005-08-09
Hi Thresher,

This is just a suggestion, not sure if it will work, but in the Control Center, under Sound & Multimedia there is a section called "Sound System".

Within that module is a tab for "Hardware", and an option to "Override device location".

I only have one sound card active, but you might want to have a look there. Also, check the config options for individual pieces of software - there is often an option to select a specific card.

Hope that helps, but if it doesn't I'm sure someone who knows will come along soon!

Best regards.

---

### Post by Thresher on 2005-08-09
I have tried using "overide device location". I'm not booted to Kubuntu right now, so I can't check for sure, but I don't think I had any luck with that, and I was just setting things fairly randomly anyway. The next time I boot to linux I'll be sure to play around with that more though.

---

### Post by Thresher on 2005-08-10
Ok, I tried messing with the sound system through kcontrol (one interesting point, I had to run 'kdesu kcontrol' to open the sound system options, otherwise kcontrol freezes).

The hardware settings I have set right now are:
audio device - ALSA
Override device location - /dev/audio1

I've tried many different 'device locations' and 'audio device' combinations, and then hitting the 'test sound' button under the 'General' tab. I've heard about not being able to play more than one sound at once or something, but I hardly ever get any sound when I hit the 'Test Sound' button, even when every other sound on the system is working.

Hopefully someone else knows how to fix this problem? II know I'm not the only one who's ever wanted to use a sound card instead of the onboard sound. I guess I could try disabling the onboard sound through the BIOS, but I don't know if that will give me what I want, or just no sound at all.

I've only been using Kubuntu for a week, so I'm not entirely sure how everything works, but I would really like someone  wiser than me to point me in the right direction. Thanks.

---

### Post by cowlip on 2005-08-10
Unfortunately, I know your situation viscerally, and I've found that Linux is universally crap in this department.  The best way is to find out what module your onboard sound card is and disable it by adding its name to /etc/hotplug/blacklist

ex., do htis in a terminal

lsmod | grep snd

Find something that sounds like an onboard sound, in my case it was snd_cmipci

sudo nano -w /etc/hotplug/blacklist

& Just add your own module there

---

### Post by Thresher on 2005-08-10
Thanks cowlip. I managed to disable my onboard sound through the hotplug blacklist, but I still have no sound. Now in my /dev there is only one 'audio', 'dsp', 'adsp', etc, but when I try to override the device location as /dev/audio and hit 'Apply' it comes up with a message saying that there is no such file or directory. It shows up under /dev when I look there but... now I'm all confused. Any help?

---

### Post by cowlip on 2005-08-11
[QUOTE=Thresher]Thanks cowlip. I managed to disable my onboard sound through the hotplug blacklist, but I still have no sound. Now in my /dev there is only one 'audio', 'dsp', 'adsp', etc, but when I try to override the device location as /dev/audio and hit 'Apply' it comes up with a message saying that there is no such file or directory. It shows up under /dev when I look there but... now I'm all confused. Any help?[/QUOTE]
  I tried to input /dev/audio as you did, and I got the same error, so I would just uncheck "override device location" and leave everything as autodetect

---

### Post by Thresher on 2005-08-11
Ok, I finally got my sound working. I was playing around with all the mixer settings, setting everything to max, and suddenly got my ears blasted off when I turned the "Audigy Analog/Digital Output Jack" off.

Seems weird considering I've seen other directions saying that some people may need to do the opposite. Maybe I have on/off confused, but I would think that when the button turns bright it would be on... it seems to work that way with the other controls anyway. I guess that control works different on a Soundblaster Live.

At any rate, thanks for the help and hopefully I know a little more about linux after this. :)

---

