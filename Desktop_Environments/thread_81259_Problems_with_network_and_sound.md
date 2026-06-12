---
title: "Problems with network and sound"
date: 2005-10-24
forum: Desktop Environments
---

### Post by Backo on 2005-10-24
Hello,
I have a problem with my network. It is configured and it is working fine but every time I log on I have to activate it. If anybody has a solution please help.
Andabout the sound problem. I have installed amaroK. All the sound engines are installed - alsa, oss, gstreamer. I configure amaroK to work with xine on alsa output, but it does not play the music. No error message is showed either. XMMS is working fine, but I like amaroK and I want to use it.
I will be very thankful for every answer.

---

### Post by taavi on 2005-10-24
Try using esd(Esound deamon or E)output. Can you hear System Sounds when logging in/out and GDM start-up sound (nice djembes) ?

---

### Post by Backo on 2005-10-24
All the sounds are fine, they are the reason to use ubuntu for the moment. Only amaroK is not playing sounds and I have no idea what is the reason for this.

---

### Post by joselin on 2005-10-24
I have the same problem... all sounds works, but rithmbox and totem does not play anything.

Regards.

---

### Post by Backo on 2005-10-24
[QUOTE=joselin]I have the same problem... all sounds works, but rithmbox and totem does not play anything.

Regards.[/QUOTE]

If you find a solution please share it. :) 
 10x in advance.

---

### Post by joselin on 2005-10-24
Sure, but now, i **still** have the problem.

---

### Post by taavi on 2005-10-24
Once again: Have you tried using **esd** (Esound) output in amaroK or other apps?

---

### Post by joselin on 2005-10-24
[QUOTE=taavi]Once again: Have you tried using **esd** (Esound) output in amaroK or other apps?[/QUOTE]

I use ESD, and i can heard all sound from gnome, from games and other apps (like gaim...) but i can't play music files on neither rithmbox or banshee.

---

### Post by emperor on 2005-10-24
[quote=joselin]I have the same problem... all sounds works, but rithmbox and totem does not play anything.

Regards.[/quote]

Do you have alsa-oss installed?

---

### Post by Backo on 2005-10-24
I have every thing linked with oss and alsa installed.

---

### Post by joselin on 2005-10-25
[QUOTE=emperor]Do you have alsa-oss installed?[/QUOTE]

Yes, i have it.

Regards.

---

### Post by emperor on 2005-10-26
Is "System - Preferences - Multimedia Systems Selector" set to:
Output: ESD
Input: OSS

---

### Post by Backo on 2005-10-26
I solved the problem with the sound.
It apears that Ubuntu has found two sound devices on my PC. Intel CH5 (or something like that) and Realtec AC97. The Intel CH5 was selected. I changed it to Realtec AC97 and amaroK started to play.
I suppose that Intel CH5 is some sort of virtual device bedause I have only the on board audio system of the motherbord - Realtec AC97.
If any body can help me for my problem with the network I will be very thankful.

---

### Post by joselin on 2005-10-26
[QUOTE=emperor]Is "System - Preferences - Multimedia Systems Selector" set to:
Output: ESD
Input: OSS[/QUOTE]

I can't do it. I only have ESD, ALSA, Silence and Custom. I tried with ESD and ALSA, but nothing happens.

Regards.

---

### Post by joselin on 2005-10-29
I need help, all sound in applications works except in banshee or rhytmbox. I can hear mp3 or off files with totem too.

I install an reinstall several times, but without success....

---

### Post by emperor on 2005-10-29
[quote=joselin]I need help, all sound in applications works except in banshee or rhytmbox. I can hear mp3 or off files with totem too.

I install an reinstall several times, but without success....[/quote] 
Do you have the following packages installed:
gstreamer0.8-mad
gstreamer0.8-oss

---

### Post by joselin on 2005-10-29
Ohhhh dear!!

I didn't have installed gstreamer-mad... after install it, it works. I believe that this package were loose in the upgrade from hoary to breezy.

Thanks a lot for your help.

Regards.

---

