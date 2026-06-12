---
title: "KDE &amp; Sound System ... Need clarification"
date: 2005-05-13
forum: Desktop Environments
---

### Post by usererror on 2005-05-13
I am really confused.  I am trying to make KDE function so that I can play mp3s via XMMS and also hear my system notification .ogg sounds.  For a while i was unable to get any sound via xmms, but I could get sound via Kontrol Center and the System Bells... until i realized that KDE takes exclusive control of the sound system, until it goes Idle...(why is that!?)

So here is my confusion: Do i have to have OSS and Alsa installed at the same time to control my sounds?

As it stands now XMMS uses the OSS driver to play Audio and KDE uses Alsa, BUT i cannot hear my system bells.  So what gives?

I thought Alsa allowed you to hear multiple sounds at the same time, but I can't get Alsa for KDE and XMMS to work hand in hand at the same time (or if i did, i can't remember i have tried so many different combos  :-? )

can somoene help me to understand this more?

my mixer tells me that OSS is mixing my SigmaTel Sound card which is what i install in windows for sound, and Also is contoling an Intel Device, which I am guessing is my microphone? 

I am very confused.   ](*,)

---

### Post by bored2k on 2005-05-13
I am a new KDE user. I had applied the patch in [http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd](http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd) to make GNOME use multiple sounds. After I ported to KDE, I am able to use eSound with XMMS. I can also use ALSA, but somethings music just stops.

---

### Post by tardis_junkie on 2005-05-13
Hope this helps.

KDE uses the arts sound daemon as a wrapper to either oss or alsa. So tu use xmms and also hear your system beep etc.,.

sudo apt-get install xmms-arts

restart xmms and from optikns - output plugin choose arts output.

And (fingers crossed) hey presto xmms plays and kde beeps

---

### Post by usererror on 2005-05-13
blasted.  i am going to primitive mode for the weekend.  I'll have to try that when I get back to work on monday. ;)  thanks for the tip though! :)

---

### Post by Beestar on 2005-05-14
[QUOTE=usererror]blasted.  i am going to primitive mode for the weekend.  I'll have to try that when I get back to work on monday. ;)  thanks for the tip though! :)[/QUOTE]
 Thanks!  This saved my day!  Works like a charm!

This leaves me with another question: why is KDE using it's own wrapper?  Why not use ALSA directly?

Thanks in advance,


Bee

---

### Post by tardis_junkie on 2005-05-14
Hi,

ALSA only allows one app access at a time - so xmms and kde could not sing together.

SO kde uses arts, and gnome under ubuntu uses esd for the same reason.

If you play xmms on a standard gnome desktop no other apps can access the sound device which is why they chose esd, allthough this has its own problems.

---

### Post by usererror on 2005-05-16
[QUOTE=tardis_junkie]Hi,

ALSA only allows one app access at a time - so xmms and kde could not sing together.

SO kde uses arts, and gnome under ubuntu uses esd for the same reason.

If you play xmms on a standard gnome desktop no other apps can access the sound device which is why they chose esd, allthough this has its own problems.[/QUOTE]

so each program that needs to play sound has to use it's own sound daemon?

by the way it works now. :D  xmms is using arts and kde is using something else.

---

### Post by bored2k on 2005-05-16
[QUOTE=usererror]so each program that needs to play sound has to use it's own sound daemon?

by the way it works now. :D  xmms is using arts and kde is using something else.[/QUOTE]
 Not necessarily. I use ESD for mostly everything, and it supports multiple uses at the same time. At least here it does..

---

### Post by Ironi on 2005-05-16
[QUOTE=usererror]so each program that needs to play sound has to use it's own sound daemon?
[/QUOTE]
You can mess around with various sound daemons and try to get every app to use the same one (good luck!). Personally, though, it's a lot easier if your sound card and driver support multiple streams, as is the case with my Audigy 2 ZS. I haven't had to concern myself with anything as trivial as multiple audio apps running since I bought it. :)

---

### Post by usererror on 2005-05-16
[QUOTE=Ironi]You can mess around with various sound daemons and try to get every app to use the same one (good luck!). Personally, though, it's a lot easier if your sound card and driver support multiple streams, as is the case with my Audigy 2 ZS. I haven't had to concern myself with anything as trivial as multiple audio apps running since I bought it. :)[/QUOTE]

currently my sound card does support sounds from multiple programs, i think, since i can play mp3s in xmms plus hear all my kde bells and whistles...

---

### Post by Ironi on 2005-05-16
[QUOTE=usererror]currently my sound card does support sounds from multiple programs, i think, since i can play mp3s in xmms plus hear all my kde bells and whistles...[/QUOTE]
Presumably, both KDE apps and XMMS are using artsd to ALSA/OSS. What I was referring to as "multiple streams" is called [hardware mixing](http://alsa.opensrc.org/index.php?page=AlsaSharing). Basically, the presence of such a feature means that I don't have to worry about whether or not apps are all using the same sound daemon. I can, for instance, play Quake 3 (ALSA OSS emu), listen to music in amaroK (ALSA via libxine), hear KDE sounds (artsd -> ALSA), and hear scripted audio events (mpg123 -> ALSA OSS emu) all at the same time.

---

