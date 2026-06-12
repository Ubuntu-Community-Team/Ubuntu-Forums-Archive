---
title: "Sound problems after going from hoary to breezy"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Beastboy26 on 2005-10-13
Ok, I am having sound problems. No sound at boot up, beep will not play any files, no "ding" when someone IM's, and no sound when clicking menu options.  I have ck'ed Multimedi Systems selector, and output is set to ALSA,  I have also tried ESD, get this error for esd: 

Failed to construct test pipeline for 'ESD - Enlightenment Sound Daemon'

I have ck'ed the volume levels for mixer and everything,
btw, Playing a CD from the cd rom works...

Thank You for any suggestions!

---

### Post by vrecan on 2005-10-13
can you tell us what sound card you have?

---

### Post by Beastboy26 on 2005-10-13
[QUOTE=vrecan]can you tell us what sound card you have?[/QUOTE]

I went to the IBM website (I bought a T43 Laptop)  and it told me nothing....

Sound Preferences says my default sound card is Intel ICH6

---

### Post by oldblue on 2005-10-13
Under Sound Preferences is the "enable sound server at startup" checked?

---

### Post by vrecan on 2005-10-13
hmm I see something in the mailing list with some other people having this problem... sorry to say but no one seems to have come up with a solution yet.    If I see anything I will report back.

---

### Post by Beastboy26 on 2005-10-13
[QUOTE=oldblue]Under Sound Preferences is the "enable sound server at startup" checked?[/QUOTE]

yep, double check it though.  Thanks

---

### Post by oldblue on 2005-10-13
Well, the only thing I can think of off the top of my head is that Beep is trying to output to the ESD sink by default.  But if you have your output set to ALSA and you have the enable sound server button UNchecked, then that may explain your problem.  If you uncheck the sound server at startup you will no longer get certain notification sounds and startup sound.  I believe it will also disable the starting of ESD at startup.  Some people set it up like this because the ESD daemon causes (or did cause) audio lag when watching movies in Totem.

---

### Post by vrecan on 2005-10-13
according to the mailing lists their are a few people who aren't getting sound at all from these chips.  This may be one of those things that slipped by the testers.  Hopefully they will find a workaround.

---

### Post by Beastboy26 on 2005-10-13
I found the solution, I fully UNINSTALLED polypaudio using synaptic, and installed esound.  Then I had to Reboot. This may be the solution for others.  I ck'ed and Beep, totem and my IM' "dings" and boot sounds all work!!! Thanks!!

---

### Post by vrecan on 2005-10-13
awesome, too bad I couldn't be of much use!

---

### Post by oldblue on 2005-10-13
Good to know!  If I remember correctly polypaudio is new to Breezy.  Apparently it doesn't work well with all soundcards.  Run the Ubuntu Device Database (under App/System...it's a kind of hardware survey).  And when you get to the sound card section add a comment on the problem and how it was fixed.

---

### Post by skagedal on 2005-10-19
I have a ST AUdio DSP 2000 C-Port sound card, and I have some different sound problems... 

After upgrading to Breezy and rebooting my system, I was met with the strangest noice! It was like some dark jungle sounds, as if from Apocalypse Now. I thought, whoaa, is this the new Ubuntu sound? Hey, kinda cool! But why is it taking soooo long time? :)

Well, I quickly noticed that something wasn't right. Trying to play music in BMP, everything was down-pitched and slow. Hmmm. So I tried "esdctl off" and a simple "play foo.mp3" - that played correctly. So Esound seems to be the problem...

But now, I read that Esound is supposedly replaced with polypaudio. It seems on my system though, that "polypaudio" is NOT installed. Esound is, and is running.

Thoughts?

---

### Post by LanceRushing on 2005-12-15
Check your groups:
```
$ ls -l /dev/dsp
$ groups
```

Make sure you are in the audio group which has permissions to write to /dev/dsp

if not:

```
$ sudo usermod -G audio [username]
```
Logout and log back in.

See [http://ubuntuforums.org/showthread.php?p=575727#post575727](http://ubuntuforums.org/showthread.php?p=575727#post575727)

-Lance

---

