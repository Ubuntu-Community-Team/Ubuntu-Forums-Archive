---
title: "Wine + Vent, mic not picking up sound?"
date: 2007-04-24
forum: Gaming &amp; Leisure
---

### Post by Big_Rog on 2007-04-24
Well, it's been about 2 months since I've made the plunge into full time Linux desktop and it's been a fairly smooth transition.  I've managed to get WoW running in OpenGL thanks mostly to the how-to's posted here.  I've tried the Vent setup info posted as well, and I can connect, hear, key up PTT from outside the vent window, but I still can't get sound to transmit.  If I blow/talk into the mic, I can hear it in the speakers, so I know that it's connected and not muted.  I've tinkered with several sound settings in winecfg, vent, and alsamixer, but to no avail.

In winecfg I have only OSS selected, vent is started with "aoss wine ~/ventdir..." and the inputs are both unmuted/turned up and selected in vent setup.  What would prevent vent from sending outbound audio?  Perhaps a screenshot of my setup would be more clear of what I have setup...

System:
nForce4 board (onboard sound), Ath64 cpu, Edgy Xubuntu.  wine is current as of posting, as is vent.

Any other details that would help?

---

### Post by rakeleer on 2007-05-14
I'm having the same problem, and have a similar setup.

So far, aoss/switching OSS and ALSA in winecfg, fiddling with WoW and Vent's mixer settings - can't seem to get this working.

I'd be interested in anyone's solution.

---

### Post by Cappy on 2007-05-14
Hearing yourself and being able to record are different things.
[http://ubuntuforums.org/showthread.php?p=2306168](http://ubuntuforums.org/showthread.php?p=2306168)

I also had to use the sidenet script, although I'm not sure what you might lose if you run it. I think it might delete your current registry, so you should at least have a backup of any specific registry folders you need if you do end up using the script.
[http://ubuntuforums.org/showthread.php?t=185557](http://ubuntuforums.org/showthread.php?t=185557)

---

### Post by oly on 2007-05-14
i got it working, but its rather unstable and not quite sure what settings i am using now.

make sure you have a mixer in wincfg under alsa and also make sure you are running aoss and launch ventrilo with aoss wine ventrilo.exe.

in ventrilo setting i have output device dmix:0 and dsnoop:0 and C-media under mixer mux and line settings do not seem to be needed. 

also use push to talk i had trouble with auto pick up when talking, ventrilo also needs to be in focus to work.

i am also using the latest wine from the wine repo if thats any help, much more than this i can not help with, mess about loads thats how i got it to work.

or use teamspeak it works a lot better, but use aoss teamspeak to launch it and the server is also very easy to set up. both run extremely well with feisty.

---

### Post by willskills on 2007-05-14
Hi guys - I have bcome a little bit of a dab hand at helping people to get Vent picking up sound, after trying to help a few people out........

I will be in IRC when I get home from work; irc.freenode.net #ubuntu-uk - I am willskills - please fire me a PM and I'll do my best to offer assistance!

---

