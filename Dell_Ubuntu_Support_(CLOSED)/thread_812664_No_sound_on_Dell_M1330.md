---
title: "No sound on Dell M1330"
date: 2008-05-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jberger on 2008-05-30
I can not get any sound out of my laptop (running Hardy 8.04 on Dell M1330)
Please advice me what to do! I have made every conceivable changes to
the sound settings but it does not help.

---

### Post by dakhan on 2008-05-30
Could you write your current mixer settings?

BTW alsamixer is an useful console tool to manipulate them.

---

### Post by sdennie on 2008-05-30
Did you buy an Ubuntu pre-installed machine and upgrade it to 8.04?  If so, you may want to check this link: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade)

---

### Post by jberger on 2008-05-30
I did not buy this machine with Ubuntu pre-installed. My current sound settings are as follows; Auto Detect on everything but soundcapture (ALSA) and Default mixer tracks (HDA Intel).

---

### Post by remerson on 2008-06-01
I have the same issue - brand new M1330 (2 days old).

No sound at all.

Fresh install of XUbuntu 8.04 (dual boot Vista).

Let me know if there are any details needed.

---

### Post by marlun on 2008-06-02
I'm also getting a M1330 which I've planned to have Ubuntu on and if there is problems with the sound I'd also want it to be fixed :)

---

### Post by dakhan on 2008-06-03
> **jberger said:**
> I did not buy this machine with Ubuntu pre-installed. My current sound settings are as follows; Auto Detect on everything but soundcapture (ALSA) and Default mixer tracks (HDA Intel).

You probably have some channel(s) muted... I'm using Kubuntu, so instead of variant-specific mixer setup, I recommend alsamixer in terminal - I have active (not muted) following channels: Headphones, Front, Surround, Center, IEC958 1, Analog Loopback and Swap Center/LFE. PCM channel is maxed out and Master channel is used by me to regulate the sound volume.

I have installed Gutsy using Dell reinstall DVD and upgraded to Hardy - no problems at all (with sound ;-))!

Best regards,
Andrzej

---

### Post by medley on 2008-07-17
> **jberger said:**
> I can not get any sound out of my laptop (running Hardy 8.04 on Dell M1330)
Please advice me what to do! I have made every conceivable changes to
the sound settings but it does not help.

I had the same problem. To fix it, I right clicked the KMix icon in the task tray, selected 'Select Master Channel' and changed it from Master to PCM.

Try it out.

---

