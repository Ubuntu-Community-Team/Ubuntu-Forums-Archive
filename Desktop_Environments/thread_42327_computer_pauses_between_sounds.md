---
title: "computer pauses between sounds"
date: 2005-06-17
forum: Desktop Environments
---

### Post by connellr on 2005-06-17
Hello,

Just when I thought I had the whole sound thing figured out in Ubuntu I realize I still have one major nagging problem.  When one sound ends there is a pause - not just in the sound, but the whole system.  The pause lasts like .4 seconds, but can be really annoying.  The easiest way to notice this problem is when I play a flash game that has a sound effect (such as curveball for those of you who know it).  Everytime I make a move it plays the sound for that move then my sound, video, and mouse appear to freeze for a split second then everything is back to normal until the next sound plays.

Sounds that are more streaming (ie: streaming audio, DVDs, video, mplayer, etc) all play without problems, but programs that have many quick sound effects really suffer.

Any advice?
(Problem is in both Gnome and KDE)

Thanks in advance,
RJ

---

### Post by jarrett.wold on 2005-06-18
What sound server are you using?  ESS, OSS, ALSA? 

Assuming Gnome:
Go to System->Preferences->Multimedia Selector

EDIT:  Also what sound card do you have?

As an aside if you're using customized sounds (which it doesn't seem you are), if they're corrupted that can cause definite problems.

---

### Post by connellr on 2005-06-19
[QUOTE=jarrett.wold]What sound server are you using?  ESS, OSS, ALSA? 

Assuming Gnome:
Go to System->Preferences->Multimedia Selector

EDIT:  Also what sound card do you have?

As an aside if you're using customized sounds (which it doesn't seem you are), if they're corrupted that can cause definite problems.[/QUOTE]

Sorry, I should have been more specific before, but I was in a hurry.  I have tried ALSA, OSS, TOSS, etc.  (I havent yet managed to get ESS working correctly).  I have the same problem with all of these sound servers.  I generally leave my sound-server set to "Automatic" (This is an option in KDE, not sure about gnome).  

My sound card is a SoundBlaster Live Platinum 5.1, and with the exception of this one issue is working wonderfully.

Any sugestions?
RJ

---

### Post by jarrett.wold on 2005-06-19
I would try grabbing the latest Alsa Drivers from [http://www.alsa-project.org/](http://www.alsa-project.org/)
That's how I got my Soundblaster Live 24bit working.

You can find your specific chipset on there, and it gives a list of instructions on how to get the driver compiled and working.

---

