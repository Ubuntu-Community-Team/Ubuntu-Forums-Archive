---
title: "Module snd_intel8x0 not found"
date: 2006-01-08
forum: General Help
---

### Post by kdevos on 2006-01-08
Hi,

I'm trying to install the ALSA driver to get my soudncard working on my laptop, now I manage to compile all the alsa driver files and the make install creates the snd_intel8x0.ko file in /lib/modules/2.6.12/misc/pci, but when I try to do the modprobe snd-intel8x0 I get the error 'Module snd_intel8x0 not found'. Does anyone knows shat could be causing this?

My 'uname -r' returns
2.6.12.10-386 shouldn't the alfa driver be installed in /lib/modules/2.6.12.10-386?
I already did a depmod -a and an update-modules but breezer does not find the module.

thx a lot

---

### Post by aclaunch on 2006-01-08
Why are you installing ALSA by hand; why not just use Synaptic/apt-get?

More info will help to figure out what is going on.

Alan

---

### Post by kdevos on 2006-01-09
Hi,

Thx for the reply, I tried to do apt-get install alsa-base 1.0.9b-4 but I get no errors on install en lsmod still does not return the module alsa, while doing a nex apt-get install indicated that there is already a version installed. Nevertheless I get no error on my Laptop HP NC8000 with this soundcard: '0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)'

the soundcard shows up in the compatibility list

pls help

---

### Post by AndriusKulikauskas on 2006-01-19
Hi, I'm also having problems with snd_intel8x0 .  I have a new BareBone laptop with an ICH6 AC'97 82801FB/FBM/FR/FW/FRW sound card.  I installed Ubuntu Breezy Badger but I don't have any sound at all.  I've searched for information about snd_intel8x0 and see that there are issues reported, but I don't see any clear solutions.  However, there are reports of people getting it to work.  Where do I start?  Also, what is the simplest way to check sound?  There seem to be so many ways that the sound could be turned off unintentionally, and no easy way to create a test sound that I know of - that would be helpful for diagnostics (much like ping is for networks).  Please help!  Thank you!

---

