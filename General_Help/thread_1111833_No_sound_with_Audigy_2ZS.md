---
title: "No sound with Audigy 2ZS"
date: 2009-03-31
forum: General Help
---

### Post by kmac20 on 2009-03-31
Hello all, how is everyone this morning?

I recently installed ubuntu in dual boot with windows vista (recently as in tonight).  While I have had some previous outings with linux, it was with openSUSE, and not too in depth, so bear with my lack of education regarding everything.  Anyway, onto my problem:

I have a Soundblaster Audigy 2ZS, I have speakers, yet I have no sound.  In a program, in firefox, in the sound preferences tab where you can click test, nada.  I have installed necessary codecs, spent awhile googling and searching these forums for answers, and while I have seen that some people have had success, I unfortunately am not.

I have tried installing ALSAmixer (although to be frank, I'm not sure what else to do with it exactly), and setting everything to use that, however, I have had no luck.  The speakers are definitely working though, as in Vista I have sound no problems, and have had it in the past when I have used suse (over the summer).

I am using ubuntu 8.10 64 bit, and the card as stated is an Audigy 2zs, speakers are 5.1 surround sound.  

Any help would be great, and I'm willing to do whatever it takes to get sound coming out of my speakers in ubuntu.  

Thanks in advance to anyone who can help me out.

---

### Post by pgmer6809 on 2009-03-31
> **kmac20 said:**
> Hello all, how is everyone this morning?

I recently installed ubuntu in dual boot with windows vista (recently as in tonight).  While I have had some previous outings with linux, it was with openSUSE, and not too in depth, so bear with my lack of education regarding everything.  Anyway, onto my problem:

I have a Soundblaster Audigy 2ZS, I have speakers, yet I have no sound.  In a program, in firefox, in the sound preferences tab where you can click test, nada.  I have installed necessary codecs, spent awhile googling and searching these forums for answers, and while I have seen that some people have had success, I unfortunately am not.

I have tried installing ALSAmixer (although to be frank, I'm not sure what else to do with it exactly), and setting everything to use that, however, I have had no luck.  The speakers are definitely working though, as in Vista I have sound no problems, and have had it in the past when I have used suse (over the summer).

I am using ubuntu 8.10 64 bit, and the card as stated is an Audigy 2zs, speakers are 5.1 surround sound.  

Any help would be great, and I'm willing to do whatever it takes to get sound coming out of my speakers in ubuntu.  

Thanks in advance to anyone who can help me out.

I have an Audigy 2 ZS also; I did manage to get it to play sounds, but never to record. I corresponded with the Alsa maintainer, but nothing back yet.
My solution was to go the the 4SOUND web site (look it up) and download and install the latest version of OSS drivers. Then I blacklisted ALSA, and un-blacklisted OSS. Everything works smoothly now.
I put a post up about this, titled 'OSS works ALSA doesnt' in the multimedia forum. Do a search on pgmer6809

pgmer6809

---

### Post by mc4man on 2009-03-31
This may or may not help (switching off the audigy analog/digital jack

[http://ubuntuforums.org/showthread.php?t=1053058&highlight=audigy2+zs+sound&page=2](http://ubuntuforums.org/showthread.php?t=1053058&highlight=audigy2+zs+sound&page=2)

With my 2zs and a 5.1 sound system I eventually removed pulseaudio (and libpulsecore5) due to terrible performance when upmixing 2 channel sources to 6 ch output with some third party apps (worked fine with gstreamer apps, but I don't use them

---

