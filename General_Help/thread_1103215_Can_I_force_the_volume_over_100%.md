---
title: "Can I force the volume over 100%?"
date: 2009-03-22
forum: General Help
---

### Post by gaiterin on 2009-03-22
Hi!
I have a monitor TFT with speakers.
This monitor has a normal volume, I like a little more volume, I like force the volume over the 100% in ALSA, to by example 115%.
Can I do it?
Thanks very much!

---

### Post by issih on 2009-03-22
Um no 100% is the most you can really hope for, its the maximum limit.

You can't get more than 100% in anything ever, by definition.

You could try a little amplifier in line with the monitors speakers, but you could blow the speaker drive units if you aren't careful.

---

### Post by cubeist on 2009-03-22
woah, this is like an existential question...does 115% actually exist...

Anyway, you could try opening alsa mixer, in a terminal, type
```
alsa mixer
```
In that window you will see two different sliders, one for PCM and one called Master, it may be that your master is at 100%, but the PCM is down low...not sure if this will help, just a thought...

---

### Post by gaiterin on 2009-03-22
Yes, all it at 100% ;)
I can see too the same problem in a laptop (not me laptop), the volume was more slow, and I was thinking if I can force it (by my responsability of crashs the speakers) ;)
Thanks by answers!

---

### Post by jocko on 2009-03-22
I'm pretty sure if you set everything to 100% in alsamixer, you are really maxing out the output from the soundcard.
There's no way for any piece of software to magically increase the capacity of your hardware. Connect it to an external amplifier with bigger speakers if you want more (and probably better) sound.

---

### Post by gaiterin on 2009-03-22
Can I not amplify the volume for software?

---

### Post by cubeist on 2009-03-22
No, if everything is at 100%, then that is as loud as it will get.  Your only option is to get a more powerful (ie watts), amplifier.

---

### Post by MaxIBoy on 2009-03-22
> **gaiterin said:**
> Can I not amplify the volume for software?Some audio players (Audacious is one of them) let you set the "gain," but it's really not going to help you much. If you set the gain really high, the sound will be "clipped" due to the maximum voltage of the soundcard, and you might also "overdrive" the speakers. Have you ever used a weed-whacker, and the wires hit a rock? That's basically what clipping sounds like. Overdriven speakers are even worse.

---

### Post by gaiterin on 2009-03-22
Ok ;)
Thanks very much to all for the answers!!!
Cheers!

---

### Post by chriskin on 2009-03-22
isn't vlc capable of making the sound be at 200% without any problem?
so i have noticed at least...

it is not a speaker problem usually that the sound is too low, windows has it way louder than ubuntu.

so some software might be able to make it sound louder without any problem to the sound or the speakers 

(jaunty has it loud enough, or so it seems, if you do not care fiddling with aplha versions)

---

### Post by jocko on 2009-03-23
> **chriskin said:**
> isn't vlc capable of making the sound be at 200% without any problem?

That's just a software volume control which can amplify the output of sound files with too low recording volume. The soundcard will still not be able to output more than 100%. Setting vlc to more than 100% will just distort everything that would be above 100% of the sound card's capacity.

---

### Post by chriskin on 2009-03-23
> **jocko said:**
> That's just a software volume control which can amplify the output of sound files with too low recording volume. The soundcard will still not be able to output more than 100%. Setting vlc to more than 100% will just distort everything that would be above 100% of the sound card's capacity.


i insist that it is not limited by the sound card
both pc-bsd and windows has way louder sound than ubuntu

---

### Post by Rallg on 2009-03-23
You could be like "Spinal Tap" and paint 110% over the volume control. :guitar:

---

### Post by themusicalduck on 2009-03-23
For a slightly different way of looking at it, you could see if you can find a software based audio compressor? If you compress the audio a bit it should sound a little more 'boosted' without distortion, but you'll also lose some dynamic range in the audio. Not sure if such a plugin exists for amarok or something like it.

---

### Post by ibuclaw on 2009-03-23
I'm not entirely sure how VLC's built-in Equaliser works for compression.

But if you install **jamin** (along with jackd and qjackctl) you could pipe all audio through a Digital Audio Mastering Application :)

Although, be prepared not to have the most stablest of sound systems if your soundcard isn't great at realtime (just increase the periods/buffer. Latency isn't a mission critical issue since you'll most likely only want to only use output rather than full duplex soundcard I/O ... IMO, 50m/s latency is what you are looking to at least have.)

[EDIT]
Here is a screenie :)
[http://img23.imageshack.us/img23/8491/screenshot5hzl.png](http://img23.imageshack.us/img23/8491/screenshot5hzl.png)

Regards
Iain

---

### Post by jocko on 2009-03-24
> **chriskin said:**
> i insist that it is not limited by the sound card
both pc-bsd and windows has way louder sound than ubuntu
Then if you have set all volume sliders in alsamixer to 100%, it's probably a driver problem. The maximum volume in alsamixer is always going to be the limit, even if the sound card is physically capable of more.
Maybe you should ask if anyone else have the same problem with the same sound card/driver? If it's a common problem with your card, maybe there is a fix somewhere...

---

### Post by Stagger Lee on 2009-04-18
> **chriskin said:**
> i insist that it is not limited by the sound card
both pc-bsd and windows has way louder sound than ubuntu

Yes I agree. My HD has 2 partitions, one with Ibex the other with XP. 
The same file (video, streaming audio, mp3, anything) will have a considerably lower volume output on Ubuntu. 
I have done lots of searches on drivers, but nothing seemed to work. 
I, too, was actually thinking a little software giving me a tiny bit extra gain would work just fine, but I am not sure how I would accomplish that. 
Also I noticed that VLC plays files slightly louder than Totem. 

It's not like the sound it's inaudible, but sometimes you want to go and turn it up a bit and - god, it's all the way up already. Like someone was saying, one thinks of the Spinal Tap, and damn, my laptop doesnt go up to 11 :)

As for my soundcard info, what i get from Sysinfo is: 
[I]
Intel Corporation 82801G (ICH7Family) High Definition Audio Controller (rev 02)
Subsystem: Fujitsu Siemens Computers Device 10c1[/I]

My laptop is a Fujitsu Siemens Amilo Pro. 
Anything in common with the other people here having the same issues?
I hope we can get this sorted out somehow. :D

---

