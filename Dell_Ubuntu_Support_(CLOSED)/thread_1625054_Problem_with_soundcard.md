---
title: "Problem with soundcard"
date: 2010-11-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Arnold Layne on 2010-11-18
I've just installed Ubuntu 10.10 on my Precision 350 and my soundcard does'nt work. Ubuntu can't detect the onboard soundcard at all. Somebody got a clue how to fix this problem?

---

### Post by Arnold Layne on 2010-11-21
*bump*

---

### Post by combatkenpo66 on 2010-11-23
I had the same issue and deleting pulseaudio did the trick for me.  Once that was gone, ALSA picked up the card and is working wonderfully.

---

### Post by Arnold Layne on 2010-12-19
Thanks!
But it's been three years since I used Ubuntu, so how do I remove pulseaudio?

---

### Post by jwaclawsky on 2010-12-20
I can see it in the Synaptic Package Manager and it appears you can  install or remove it from there.
System > Administration >Synaptic Package Manager

---

### Post by lidex on 2011-01-05
Old thread?
FWIW I would respond to the initial post with this:
Re-install alsa:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
Remove old config files:
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**

---

