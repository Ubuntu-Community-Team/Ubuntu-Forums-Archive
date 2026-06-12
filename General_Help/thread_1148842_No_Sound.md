---
title: "No Sound?"
date: 2009-05-04
forum: General Help
---

### Post by zamadatix on 2009-05-04
I ALWAYS have sound in Xubuntu/Ubuntu but in Xubuntu 9.04 for some reason I do not have sound. It says there are no restricted drivers and I never remember having to download sound drivers for ubuntu previously.

---

### Post by lemcoe9 on 2009-05-04
Go to Applications > System > Hardware Drivers, and it will install any restricted drivers it thinks it needs there. I had to do a similar thing with my nVidia card saying it was restricted. 

Good luck

David

---

### Post by zamadatix on 2009-05-04
> **zamadatix said:**
> It says there are no restricted drivers
Thanks but I already checked, nothing there :P.

---

### Post by utnubuuser on 2009-05-04
At the risk of sounding ignorant..

I guess nothing is muted?

---

### Post by zamadatix on 2009-05-04
I can not find a volume meter or sound settings area anywhere so it is actually a good question... normally you would expect a sound icon in the panel would not you? or at least the preferences menu?

EDIT: Actually that was it, I found the sound thingy in the add list and for some reason every item was unchecked and muted! Thank you :)

---

### Post by paradigm2 on 2009-05-04
> **zamadatix said:**
> I ALWAYS have sound in Xubuntu/Ubuntu but in Xubuntu 9.04 for some reason I do not have sound. It says there are no restricted drivers and I never remember having to download sound drivers for ubuntu previously.

If you can from a terminal:

```

lspci

```

Check to make sure it simply isn't muted or that the volume isn't turned down in alsa or pulse audio.

Usually you can access this by running:

alsamixer
alsamixergui

or

gnome-alsamixer (I believe this is it, if not go into synaptic and do a search for alsamixer and install the one which you like best then make sure it isn't muted)

Also check your sound preferences to see if you have either ALSA or OPulseaudio selected, as well as the proper device.

I would give you a step by step but am at my gentoo box now soI cannot.  You may want to install pavucontrol (I believe is the name) as well as pavuvolume (Again, nto sure on name -- I use alsa only on this box but do a search for "pavu" in synaptic)

---

### Post by OMJD on 2009-05-04
There's some really bad sound bug in 9.04 which basically lowers the volume right down. It's so bad that when using my headphones, I can't hear a thing. I can only hear sound when it's amplified through a powerful amp, and then through speakers which are designed for use in night clubs. 

I've searched the problem, but none of the solutions work for me. :(

---

### Post by paradigm2 on 2009-05-04
> **OMJD said:**
> There's some really bad sound bug in 9.04 which basically lowers the volume right down. It's so bad that when using my headphones, I can't hear a thing. I can only hear sound when it's amplified through a powerful amp, and then through speakers which are designed for use in night clubs. 

I've searched the problem, but none of the solutions work for me. :(

This is true, I had forgotten about that.   This can happen even if youhave turned up sound properly in the mixers.  Which sound card do you have?  If Intel HDA or it uses that driver it is fairly common.  In my case I upgraded the alsa and pulseaudio through a unofficial PPA and then also upgraded to the 2.6.30rc4 kernel in order to resovle the issue.

---

### Post by joepastafari on 2009-05-24
I spent hours trying to fix this problem.  For me, at least, the system speaker was taking everything over, so I added the following to /etc/modprobe.d/blacklist.conf:
blacklist snd_pcsp
reboot, and bam, sound works awesome.  Hope this helps someone.

---

### Post by joepastafari on 2009-05-24
on a somewhat related note, in order to amarok to play correctly, I had to install phonon-backend-xine.

---

