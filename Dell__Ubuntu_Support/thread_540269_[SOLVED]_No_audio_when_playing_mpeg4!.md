---
title: "[SOLVED] No audio when playing mpeg4!"
date: 2007-09-01
forum: Dell  Ubuntu Support
---

### Post by inchaos on 2007-09-01
I've noticed a weird issue--when I play mpeg4 video I have no audio!

I've got a Dell Inspiron 1420 n and I was originally just using movie player.

I thought maybe the program was my problem, maybe I didn't have the appropriate codec or the program wasn't designed for mpeg4 support, so I tried VLC and movie player with xine...to no avail!

Not sure if this is a sound card issue or just me being stupid (I'm not the best with Linux after all) but I couldn't find anyone else experiencing the same problem.

My hardware manager lists me having an ALSA controller and an OSS controller...it also says I have AT-style speaker sound...but I'm not quite sure what any of that means.

I've got Feisty  though I had attempted to preform a kernal update to fix the hdd halt bug I was experiencing...it fixed the bug, but nothing shows that I have a different kernal.  I don't know if this is relavent but I thought I'd include as much info as I could about my system.

Any help would be greatly appreciated!

---

### Post by robotii on 2007-09-01
Have you tried all the usual stuff like checking the volume is up etc??

If so you might want to change the output layer in vlc to use OSS or ALSA, this can be found in preferences. ALSA is the more modern sound layer. Also it might help if you could post what the sound card is, as someone may have that sound card working properly.

---

### Post by inchaos on 2007-09-05
Yes, the volume is up. :)

What makes this extra weird is that it started out with no sound for videos but I could still play music, but now I have no sound at all, at any time.

As far as the sound card goes, the only description I ever received from Dell was that I had 'Integrated High Definition Audio 2.0'.  

My hardware manager lists the device as 82801H (ICH8 Family) HD Audio, the vendor as Intel.  The driver is HDA Intel.

---

### Post by inchaos on 2007-09-05
And one more thing, just in case it is relavant:
any time I come back from standby or hibernate, the volume control unexpectedly quits and I am prompted to reload it.

---

### Post by inchaos on 2007-09-11
Is anyone else having a similar issue?

I tried reinstalling the ALSA driver, to no avail.  
My computer is recognizing my sound card but refuses to output any sound.

Headphones work, so it seems that my sound card is functioning...at least partially?

---

### Post by notwen on 2007-09-11
> **inchaos said:**
> And one more thing, just in case it is relavant:
any time I come back from standby or hibernate, the volume control unexpectedly quits and I am prompted to reload it.

Check out this [thread]("http://ubuntuforums.org/showthread.php?t=530177") with users having similar issues, a link to the dell website a couple of posts down should provide a work-around.  Have you double-checked your volumes in 'alsamixer'?

---

### Post by inchaos on 2007-09-11
Yes, alsamixer volumes were at about 80%.
Not the issue, sadly.  That would be too easy. Lol.

---

### Post by inchaos on 2007-09-11
I tried the fix you recommended to no avail. 

Thanks for trying, I appreciate it.
:)

---

### Post by inchaos on 2007-09-11
Well, I figured out how to make it work, however, I don't know exactly why it wouldn't work before.

I followed a guide to compile a new kernel and was running 2.6.22

When I revert to 2.6.20 my sound works.  I also have a different version of alsamixer by default, for whatever reason.

Sooo, does that mean that I'm going to lose sound if I install Gutsy?

---

