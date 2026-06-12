---
title: "Would LOVE to get TS and TC:E (Enemy Territory mod) working together"
date: 2006-09-25
forum: Gaming &amp; Leisure
---

### Post by tonyisntcreative on 2006-09-25
I've posted a similar thread [here,]("http://ubuntuforums.org/showthread.php?p=1541430#post1541430") but I realized it would probably be more fitting in this area.

The problem is that I can't get both programs to produce sound simultaneously.  Being that I just joined a clan I more or less *need* to have both up and running.  I suppose I COULD play with only TS and have no in-game sound, but I would probably play like garbage and it'd be a waste (not being able to hear the direction of gunfire, footsteps, etc).

The problem is obviously that both programs hog the soundcard (integrated sound on an ASUS A8N-E - realteck ALC850) which doesn't have hardware mixing.  From everything I've read about, ALSA supports software mixing as long as both programs are bothing using ALSA (not one ALSA, one OSS).  I know that I can get sound mixing when both are using ALSA because I can play two sound making things at the same time (for example, BMP and Totem can both play files at the same time as long as BMP is set to use ALSA). 

Herein lies the problem, as far as I can tell.  Both (I think...at least one) of these programs uses OSS and not ALSA.  Everything I've read says that TeamSpeak uses OSS, and since I have to use the command below before I can hear sound in ET or TC:E, I assume it also uses OSS.

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

I guess software mixing is unavailable using OSS.  I have read something of ALSA emulation with the command "modprobe snd-pcm-oss > /dev/dsp," but this doesn't seem to solve my problem.

Is there any way I can get both of these programs to get along?  So far everything I've read has led me nowhere.  I will provide anyone with any information that would be helpful in resolving this.  

The only other possible solution I can come to is buying another cheap, PCI sound card and having each program use a separte card, but with this I'm afraid I would have no way to hear both through the same set of headphones, which would be a new, equally annoying problem.\

Any help is greatly appreciated.

---

### Post by jdunn on 2006-09-25
If you find an answer to this, I'd greatly appreciate if you'd share it with me.  Teamspeak is an older program and only supports OSS.  OSS does not share sound devices.  I guess you got most of your info here:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound)
I wasn't interested in changing and linking my devices and I'm not sure what 'echo' is all about.  The most promising idea I saw was to use an ALSA-OSS wrapper for Teamspeak.  However, I tried it and it didn't work for me.

I'm not sure when Teamspeak3 will be released but I hope it supports ALSA.

---

### Post by tonyisntcreative on 2006-09-25
Yes, that's one of many links I've come across in relation to this problem.

If by ALSA-OSS wrapper you mean starting the program with the command "aoss teamspeak," yeah, that didn't work for me, either.

I think one of the "problems" lies in the fact that I think I'm the only person using Linux out of all the people in the clan.

---

### Post by skirkpatrick on 2006-09-25
I have a write-up on my clan's forums on how to handle this.  I've been using TS and TCE for quite some time now.

[http://www.madinfiltration.com/bb/viewtopic.php?t=7530](http://www.madinfiltration.com/bb/viewtopic.php?t=7530)

---

### Post by tonyisntcreative on 2006-09-25
No luck.  The only thing different about that method is the last line of those three commands.  I've been using the first two for quite some time, the last one with the pcm1c is the only new one to me.

Anyone else?

---

### Post by skirkpatrick on 2006-09-26
Did you disable ESD through System->Preferences->Sound?

---

### Post by jdunn on 2006-09-26
> **tonyisntcreative said:**
> If by ALSA-OSS wrapper you mean starting the program with the command "aoss teamspeak," yeah, that didn't work for me, either.

Yes, I Installed the ALSA-OSS package and then modified the game script to something like "aoss /game-directory/teamspeak.bin".  It didn't work.  ](*,)

On a different note, where is everyone getting these similar tux avatars like you have?

---

### Post by tonyisntcreative on 2006-09-26
I had not disabled ESD, and I'm not sure whether you were instructing me to do so or rather leave it enable.

Not being sure I DID go ahead and disable it to see if it did anything different...it did not.  If I start up team speak and then start up the game, there is no sound from the game.  If I start up the game and then start up TS, then both my microphone and my speakers are muted.

I hope there is a solution to this problem.

---

### Post by haxer on 2006-09-26
OMG  [http://www.katanoon.nl/ubu-e/](http://www.katanoon.nl/ubu-e/)

---

### Post by tonyisntcreative on 2006-09-26
I'm not really sure what you're getting at.  Is there a solution to my problem somewhere on that site?

---

### Post by jdunn on 2006-09-26
I have Kubuntu.  There's no ESD, its aRTS for KDE.  Anyway, i'll read the writeups recently linked to this thread.

---

### Post by skirkpatrick on 2006-09-27
Maybe that's the difference.  I'm running Ubuntu and didn't have to do anything more that what I posted on our clan site.

The avatars are at [http://tux.crystalxp.net/](http://tux.crystalxp.net/)

---

### Post by jdunn on 2006-09-27
> **skirkpatrick said:**
> I have a write-up on my clan's forums on how to handle this.  I've been using TS and TCE for quite some time now.

[http://www.madinfiltration.com/bb/viewtopic.php?t=7530](http://www.madinfiltration.com/bb/viewtopic.php?t=7530)

I tried your write-up for two games:  ET and Savage.  It worked for niether one...I get no game sound as long as I'm running TS.  I'm using Kubuntu and I have aRTS enabled because I like to have system sounds.

I'm confused.  Teamspeak has to use the combined capture/playback device while the game (Enemy Territory in this case) has to use a seperate playback device on the same sound card.  In your write-up, it looks like you are disabling capture in devices 0,1 but you are enabling playback in 0 for ET.  This doesn't make sense to me.  Doesn't Teamspeak need to use device 0?

echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm1c/oss 

I have sound on the motherboard of my linux machine.  Unfortunately, I'm no longer certain it will work at all with TS.  I have a combined playback/capture device and a dedicated playback device...but the playback device (pcm4p) seems to be part of the S/PDIF controller and it has no OSS.

00-00: Intel ICH : Intel ICH5 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : Intel ICH5 - MIC ADC : capture 1
00-02: Intel ICH - MIC2 ADC : Intel ICH5 - MIC2 ADC : capture 1
00-03: Intel ICH - ADC2 : Intel ICH5 - ADC2 : capture 1
00-04: Intel ICH - IEC958 : Intel ICH5 - IEC958 : playback 1

Here's another reason I'm confused:  I have another computer that I normally run M$ Windows on.  It has a Soundblaster Audigy 2Zs.  I ran the Kubuntu Live CD on this computer and checked all the sound devices.  The combined playback/capture device has OSS but all the other dedicated playback devices don't have OSS.  ](*,) 

Do I need a new sound card for my Linux machine?  What's the cheapest available?  Will a SoundBlaster Live work?

**Update** 
I tried running TS and games with the aRTSd wrapper.  This actually worked but the sound delay in games and in TS, due to the wrapper, is unacceptable for me.  I'm still looking for a better solution.

---

### Post by skirkpatrick on 2006-09-27
You are beyond me now.  I actually got those settings from another post here in the forums a long time ago.

---

### Post by jdunn on 2006-09-28
> **skirkpatrick said:**
> You are beyond me now.  I actually got those settings from another post here in the forums a long time ago.

Yesterday, I purchased and installed a SB Live 24-bit to replace my on-board sound.  Using the SB, I had no sound in ET at all (with or without TS).  I checked the forums and found a script that's supposed to fix that problem...Its the script you use.  So that's what its for.  I still can't get TS to work with anything though.

---

### Post by Izuil on 2006-09-28
I have the same problem as you!
It's a real pain in the ***... I also have a integrated AC'97 but i have 650.

I to would really appreciate a solution to this problem I was even in a computer store toady wondering if i should buy myself a new sound card...

Maybe I will anyway tomorrow :)

---

### Post by tonyisntcreative on 2006-09-28
I'm beginning to think it's almost hopeless.

---

### Post by jdunn on 2006-09-29
Well, I started out with onboard sound.  Then I tried a SB Live 24-bit for a few days, assuming it would have hardware mixing because it was a 'SB Live' card.  Now I've graduated to a SB Audigy2 ZS and have everything working perfectly.  

I hate Creative Labs...They used to make SB Live Value with hardware mixing for <$30.  Now, only their high end cards have hardware mixing and the cheapest one (the Audigy2 ZS) starts at around $70-80.

---

### Post by skirkpatrick on 2006-09-29
That rings a bell.  I believe you have to have a card that supports hardware mixing.  However, I am using my onboard sound (it's a Via chip).  I feel for you about Creative.  They used to make some good, low-end cards.

---

### Post by tonyisntcreative on 2006-09-29
So I'm going to have to spend 70-80 dollars just to get two programs to play nicely?

I'll pass.

---

### Post by jdunn on 2006-09-29
> **tonyisntcreative said:**
> So I'm going to have to spend 70-80 dollars just to get two programs to play nicely?

I'll pass.

I've heard it is possible to do it without hardware mixing but it currently involves some compromises, alot of headaches and no guarantees.  The easy and sure method to have  programs "play nicely" is to have a sound card with hardware mixing and solid linux drivers.  [www.alsa-project.org/alsa-doc/](www.alsa-project.org/alsa-doc/) should help you find a suitable card (You'll find Sound Blaster cards if you select "Creative Labs" as a manufacturer).  Also, if you're lucky and resourceful, you may be able to find someone selling an old used or refurbished Sound Blaster Live card online for $10-15.  The newer low-end cards like the SB Live 24-bit, Audigy Value and SE cards are crap so don't buy any of them for your linux machine if you want to run programs like TeamSpeak.  
Good Luck

---

### Post by McLoud on 2006-09-30
I use ubuntu with alsa as the main card driver (audigy value), and I use artsd to mmaped IO:

artsd -A alsa -F 16 -S 128 &
artsdsp /usr/local/TeamSpeak/TeamSpeak.bin &
artsdsp -m et

The F and S values can be tweaked, these gave me no sound lag, but there is still some sound glitches sometimes when there is a lot of sound played together.

---

### Post by jdunn on 2006-09-30
Before I installed my hardware-mixing sound card, I tried out artsdsp...It didn't work out for me.  I decreased the sound buffer to the minimum but there was still a noticable sound delay.

---

