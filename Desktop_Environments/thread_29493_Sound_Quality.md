---
title: "Sound Quality"
date: 2005-04-24
forum: Desktop Environments
---

### Post by tyke on 2005-04-24
Hi, I have a sound problem with Kubuntu Linux.

All of my MP3s sound horribly distorted when played under Kubuntu. Theres lots of crackling and excess noise. They all play fine under XP, so I know it's not the hardware thats at fault. I'm using the intergrated audio on a Gigabyte GA7VA mother board. It's a realtek AC '97.

I've fiddled with KMix, and found that the distortion does go away if I turn things down somewhat, but the problem then is that the music is far quieter than I want it. I've tried various combinations with all the sliders in KMix, but cannnot find any way to get the sound to play at the same quality and volume windows XP manages.

Can anyone suggest anything I might want to try?

---

### Post by Firetech on 2005-04-24
Try turning PCM (may be wave or something) down to about 70-75%, and then control your volume with either the Headphones/PCM2 channel or the main volume channel. That works for me, without any crackling.

---

### Post by tristure on 2005-06-20
Tyke, have you been able to find a solution to your problem?

Have you tried other Linux distributions? Did they have the same sound quality problems?

I'm asking this because I switched from Windows to Linux two years ago. I have tried several distributions (Mandrake, Gentoo, Arch, Kubuntu) and none provided me with good sound. I even tried different soundcards!

For instance, I had a cs46xx card which worked really bad. Whenever I would start my box the sound was distorted and hardly audible. Restarting alsa didn't change anything, but rebooting the computer did. So whenever I turned my box on, I knew the first thing I would do was rebooting to have an acceptable sound quality. And even then the quality was not so good...

I tried another sound card (Sound Blaster PCi 128) : the sound quality doesn't change when I reboot, it's always bad... I hear a lot of static and crackles...
Then yesterday I booted windows for the first time in ages, and the sound was... wow... crystal clear!!

So for me it seems that this is not distribution-related, nor hardware-related, but sound really doesn't work for my system in Linux.

I don't really feel like switching back to windows, but hearing such a difference in sound quality is painful, especially given the fact that I'm a music addict!!

---

### Post by peter07 on 2005-06-23
I use Ubuntu 5.04 - Hoary. I have the same problem with sound. Turning PCM down to about 70-75% works, but it is not a good solution. What may couses bad sound quality?

---

### Post by altorus on 2005-06-23
As a long time linux user, i've found that some soundcards are just funny like this.

The windows mixer, with full driver support is fine, of course you can max every channel without distortion.  Linux however is not the same.  You just need to play with the mixer a bit to get a clean signal on some cards.

As an example, i've never come across a card that is clean at PCM 100%, its just one of those things.  This is a driver thing more than anything else.  Yes ALSA works and it is brilliant, but these are not official drivers people, sometimes there are glitches like this.

---

### Post by DancingSun on 2005-07-01
Yes, I think the best solution is reliable sound drivers from the manufacturers themselves...but that's something that is hard to convince them to do...unless Linux gains a significant share of the market....ah....it's the chicken or the egg problem again... ](*,)

---

### Post by Henk Bos on 2005-07-02
In the main configuration application of KDE, just turn on Threaded Open Sound System under
  Sound and Multimedia->SoundSystem->TAB Hardware 

Make sure that you also hava activated under TAB General that the souns system my be automatically interrupted every 10 sec.
Sorry, I use the Dutch translation, so the names might be a bit different

---

