---
title: "Ripping Mp3 with Grip?"
date: 2005-02-27
forum: Desktop Environments
---

### Post by TopDog on 2005-02-27
Alright.... here is the deal:

My Mp3 player plays Ogg. No problem ripping. But my girlfriend has an iPod, and they don't take Ogg.

In Grip, no matter what Encoder I chooce besides Ogg, I get **Invalid encoder executable. Check your encoder settings**.

I've installed **lame**, **gstreamer0.8-lame** and **liblame0**. Still no go...

With Sound Juicer, I can rip, no problem, but 256bit is way to much, the Mp3 files is around 9MB in size, and that is overkill. Haven't found any way to change this!?

With RipperX I can rip with no problem, but it doesn't relly look that good. So I would really like to use Grip, as I'm used to Grip from my previous distro's.

I've Searced the forum here and done must of the things I've found, but still no go. Anyone have any thoughts?

---

### Post by scoon on 2005-02-27
Hey there, 

Have you gone through Grip's set up to check that it has selected the encoders that you have installed ?

scoon

---

### Post by TopDog on 2005-02-27
[QUOTE=scoon]Have you gone through Grip's set up to check that it has selected the encoders that you have installed ?[/QUOTE]
Yes, I have 7 choices, 1 Ogg, one Flac and 5 different Mp3's, including Lame. Same result with everyone except Ogg.

Using Lame works fine in ripperX... strange!?

---

### Post by scoon on 2005-02-27
Hey there, 

And you made certain that grip has the correct path to lame ?

scoon

---

### Post by TopDog on 2005-02-27
[QUOTE=scoon]And you made certain that grip has the correct path to lame?[/QUOTE]
Where do I check that?

---

### Post by scoon on 2005-02-27
[QUOTE=TopDog]Where do I check that?[/QUOTE]

Hey there, 

Just were you checked that grip is using lame.  Under the config tab...

scoon

---

### Post by astoltz on 2005-02-27
At the command line try: ```
which lame
``` My system responds with "/usr/bin/lame" and that is what should go in the config tab for Grip.  If yours is something different, put that in Grip, and if it doesn't respond at all, try re-installing lame.

---

### Post by TopDog on 2005-02-27
[QUOTE=astoltz]At the command line try: ```
which lame
``` My system responds with "/usr/bin/lame" and that is what should go in the config tab for Grip. [/QUOTE]
Thanks, that did the trick  8)

---

### Post by nicholaspaul on 2005-03-09
Can you tell me what your settings are in Encoder config?
I'm looking at Encoder command line , file extension and file format which I shouldn't have changed from default!!!

---

