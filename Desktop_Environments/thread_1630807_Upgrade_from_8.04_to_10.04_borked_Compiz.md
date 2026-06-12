---
title: "Upgrade from 8.04 to 10.04 borked Compiz"
date: 2010-11-25
forum: Desktop Environments
---

### Post by WildeBeest on 2010-11-25
The upgrade went fairly smooth, with a little effort got everything working except for Compiz.

I couldn't enable desktop effects. So I decided to completely remove compiz with Synaptic and re-install.

After removing compiz, compiz was no where to be found in Synaptic.

Where did it go? How can I get compiz back?

I have a NVIDIA GeForce 8600GT video card using the 256.53 driver.

---

### Post by Helkaluin on 2010-11-25
No compiz in Synaptic?

Back to basics: check if you have the appropriate repositories enabled. (It's in universe or multiverse or something. Can't remember. Just try them all.) And do an apt-get update or equivalent.

---

### Post by Enigmapond on 2010-11-25
Go one better and add the compiz ppa to your sources and get better updates.

```
sudo add-apt-repository ppa:compiz/ppa
```

Then

```
sudo apt-get update
```

From there just go to synaptic and install everything compiz..

Cheers!

---

### Post by finlost on 2010-11-28
I am also running a nVidia 8600GT video card.  I recently upgraded to 10.04 from 9.10.  

I am having problems updating the video driver to the recommended one.  I am away from that computer right now so I don't know driver versions.  I cannot get any desktop effects to work and definitely cannot get Compiz to work.  I think I have a hardware problem as my computer suddenly powers down when I try to update the video driver or enable desktop effects.  It suddenly powers down about 3-5 minutes after updating/enabling the video.  

I have yet to research my video card problem. Anyone know if there are known issues with nVidia 8600GT with respect to 10.04?

---

