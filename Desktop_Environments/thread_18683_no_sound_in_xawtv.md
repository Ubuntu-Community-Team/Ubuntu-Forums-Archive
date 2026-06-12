---
title: "no sound in xawtv"
date: 2005-03-08
forum: Desktop Environments
---

### Post by kingofhell on 2005-03-08
im using xawtv 3.9.3 with ubuntu updated to e latest by apt-get dist-upgrade. i can see the television but theres no sound, xawtv was not muted and i can hear sound when i play mp3.

---

### Post by eternity on 2005-03-08
[QUOTE=kingofhell]im using xawtv 3.9.3 with ubuntu updated to e latest by apt-get dist-upgrade. i can see the television but theres no sound, xawtv was not muted and i can hear sound when i play mp3.[/QUOTE]

Is the TV card connected to the soundcard's line-in? If yes, check that line-in isn't muted in volume control.

---

### Post by lizardking on 2005-03-08
I have your same problem. My tuner car output audio goes to input in the microphone plug....

some help to us?
 8-[

---

### Post by eternity on 2005-03-08
[QUOTE=lizardking]I have your same problem. My tuner car output audio goes to input in the microphone plug....

some help to us?
 8-[[/QUOTE]

As I said before check that the line-in/mic isn't muted.

If that's not the problem then you need to post more details. Whith above info it's impossible to tell what is causing this problem.

---

### Post by feralert on 2005-03-09
Same thing over here!  ](*,) 

It happened to me with Warty and now with Hoary, and in two different motherboards (both with onboard sound). My tv card is a Hauppage pci card (connected to the soundcard's line-in through an external cable) and works perfectly in window$  :evil: .
I have been in many forums and seen this problem affecting many people, i dont know how it hasnt been resolved yet by the ubuntu developers since onboard sound and tv cards are so common this days  #-o .

Oh and BTW, i have nothing muted in alsamixer. I dont wanna kidnap this thread for my own problem but will post info if requested.

---

### Post by eternity on 2005-03-09
Try connect something else to the line in, mp3 player for example. If you can listen to music from line-in then you know that it isn't the soundcard causing the problem.

You can also try to connect a headphone to the TV-card line-out.

If I understand you right you have picture but no sound... To me this sounds like a soundcard problem but it might as well be a problem with the TV-card.

I  struggled alot a while ago to get my TV card working under linux and it requires some patience. Go through the documentation about TV cards in the linux kernel, just extract a kernel and look in the Documentation folder.

---

### Post by kingofhell on 2005-03-09
[QUOTE=eternity]Is the TV card connected to the soundcard's line-in? If yes, check that line-in isn't muted in volume control.[/QUOTE]
it is connected and line-in was not muted. btw im using creative audigy soundcard

---

### Post by kingofhell on 2005-03-09
[QUOTE=eternity]Try connect something else to the line in, mp3 player for example. If you can listen to music from line-in then you know that it isn't the soundcard causing the problem.

You can also try to connect a headphone to the TV-card line-out.

If I understand you right you have picture but no sound... To me this sounds like a soundcard problem but it might as well be a problem with the TV-card.

I  struggled alot a while ago to get my TV card working under linux and it requires some patience. Go through the documentation about TV cards in the linux kernel, just extract a kernel and look in the Documentation folder.[/QUOTE]
thx bro 
i connected a earphone to my tv-card's line out and theres sound. so its now confirm soundcard prob? but it works perfect in M$ windows n KDEtv

---

### Post by lizardking on 2005-03-09
[QUOTE=kingofhell]thx bro 
i connected a earphone to my tv-card's line out and theres sound. so its now confirm soundcard prob? but it works perfect in M$ windows n KDEtv[/QUOTE]

**oh yes in M$ windzoz works perfectly, damn!!!  #-o **

---

### Post by feralert on 2005-03-09
> oh yes in M$ windzoz works perfectly, damn!!! 
I tried in ubuntu to connect my speakers directly into the tvcard lineout and guess what.. At first i couldnt hear anything so i tried to put the volume to the maximun and.. SOUND !! but so very very low i wouldnt have notice it without putting it to the max.

I then tried to connect a radio to the soundcard line-in to no avail, no sound came out of my speakers. So i used gstreamer-properties and selected 'ALSA - Advanced Linux Sound Architecture' instead of the default 'ESD - Enlightenment Sound Daemon' as the audio input of the default source and the sound started to come out!! I have to say that 'OSS - Open sound system' did work as well. 

So i tried to put everything back as it was (tvcard line-out to soundcard line-in, and speakers to soundcard lineout) and tried xawtv one more, but to no avail, still couldnt get any tv sound through my speakers, i guess because the tvcard lineout audio comes out so low that its just not enought to go trough the soundcard and to the speakers.

I guess the main question is how to make the sound come louder from the tvcard line-out jack.

---

