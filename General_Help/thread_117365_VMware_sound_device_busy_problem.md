---
title: "VMware sound device busy problem"
date: 2006-01-14
forum: General Help
---

### Post by daahli on 2006-01-14
Hey guys,

I'm fooling around with VMware and the latest beta of MS Vista. I'm particularly interested in the advancements in speech recognition, but unfortunately the only thing that doesn't seem to be working is my sound device. When I boot the image, VMware tells me that /dev/dsp is busy, and that the Guest OS will therefore not have sound. 

I checked in VMware's knowledge base and it said to kill esd, which I did but it still didn't help. It must be that I'm unknowingly running some program that is using the sound device. Unfortunately I'm relatively new to linux and have not found a way to determine what program this might be. I know that there must be a specific command that will list what is currently using /dev/dsp

Hope someone can help me out!

Thanks :)

---

### Post by Madstone on 2006-01-15
Try the fuser command.  I am not certain but try fuser -l /dev/dsp
If the -l is incorrect then do man fuser at the command line

---

### Post by cesera on 2006-08-05
I had the same problem and think I solved it five minutes ago by following this howto (haven't extensively tested it yet, so I hope it fully works):
 
[http://alsa.opensrc.org/index.php?page=DmixPlugin](http://alsa.opensrc.org/index.php?page=DmixPlugin)
 
My problem was solved by step 5, but depending on your sound card you might have to go a little further (I think)
 
Hope this helps.

---

### Post by fakie_flip on 2006-08-23
Did the fuser command work for anyone? Did everyone get sound working, or are all of you still trying to get it to work? I just got VMware Server for the first time. I'd be happy if someone could help me with the sound.

---

### Post by cesera on 2006-08-23
> **fakie_flip said:**
> Did the fuser command work for anyone? Did everyone get sound working, or are all of you still trying to get it to work? I just got VMware Server for the first time. I'd be happy if someone could help me with the sound.
 
fuser did not work for me. I eventually created a ~/.asoundrc file as described in my earlier post and sound now works great for me.

---

