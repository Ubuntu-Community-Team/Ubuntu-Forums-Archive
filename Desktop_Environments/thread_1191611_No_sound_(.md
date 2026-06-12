---
title: "No sound :("
date: 2009-06-19
forum: Desktop Environments
---

### Post by AICollector on 2009-06-19
Hey all, got a bit of a problem.

I can get system sounds to play and Amarok can play music, but videos (either online or local) in any format do not play music. I've used VLC (dragon player still causes problems) and all I get is video without sound. Also, through firefox, youtube videos have no sound either. :(

I'm using Kubuntu 9.04.

Cheers for any assistance;

-AICollector

---

### Post by oobuntoo on 2009-06-19
> **AICollector said:**
> Hey all, got a bit of a problem.

I can get system sounds to play and Amarok can play music, but videos (either online or local) in any format do not play music. I've used VLC (dragon player still causes problems) and all I get is video without sound. Also, through firefox, youtube videos have no sound either. :(

I'm using Kubuntu 9.04.

Cheers for any assistance;

-AICollector

Turn up the volume setting for PCM in Kmix. Maybe that will help.

---

### Post by AICollector on 2009-06-19
Well, the PCM was zero...but no change.

It's probably worth noting that VLC plays my videos without sound, and DragonPlayer plays my videos with both video and audio...but locks up the computer!

---

### Post by asdfhjkla on 2009-06-19
Do you have more than one sound-card enabled (i.e. onboard and a soundcard)?

---

### Post by AICollector on 2009-06-19
Well, now that you mention it; I do get an odd error every time I start up, cant remember the exact wording, but it was something like;

Nvida something-something-something not working.

Falling back to Nvida something-something.

(Yes, intergrated Nvidea soundcard)

---

### Post by Freedom65 on 2009-06-19
This fixed all of my sound problems in Kubuntu 9.04. Get the Kubuntu restricted extras package. You can't use K package kit for this because it can't resolve the dependancies correctly. Open a terminal window and type sudo apt-get install kubuntu-restricted-extras. This will get you codecs for most everything. Get kaffiene player and G-Streamer engine for Kaffeine and G-Streamer plugins-good for kaffiene. Kaffiene player can be gotten through K package kit. Open Kaffiene player and select the G-Streamer engine as default. After doing all of this, I was able to play videos from my digital camera and most everything else. Hope this is helpful.

:D

---

### Post by Odemia on 2009-06-20
Sounds similar to an issue I was having.  I think it happened to me after trying out the different solutions to flash.  I have not had time to try and reproduce it.

I used 'alsamixer'  in the command line to check my Master and PCM levels, then in the System Settings>Multimedia I had to move Pulse Audio up to the top in each category.  The test button in the Multimedia is pretty handy for trouble shooting.  The last thing that was messed up in my case was the master channel in kmix somehow got set to Center (I am only using the front channels).  Had to change it back to Master, this can be done by right clicking and selecting "Set Master Channel..." and selecting "Master".

Hope you get your sound back soon.

---

