---
title: "Upgrade to lenny breaks X"
date: 2008-07-19
forum: Debian
---

### Post by dbbolton on 2008-07-19
I installed etch and had X up and running fine, using the ati driver for my video card. The only strange thing I noticed was that when GDM started up, my monitor would temporarily flash a warning "Out of Range". 

I upgraded to lenny by following [this](http://wiki.debian.org/Etch2LennyUpgrade) guide, and now I can't get GDM, or X to start. At first, I figured out that for some reason the ati driver wasn't installed anymore, so I installed 'xserver-xorg-video-ati' and tried again. No dice. 

The only warning message I saw is in the output was "No screens found". My monitor went black before showing "No input signal".  I checked my xorg.conf and everything seems to be set up the same as it was on etch.

Has anyone else had this problem or figured out a solution? Any help would be appreciated.

---

### Post by Bachstelze on 2008-07-21
Maybe your X configuration got screwed somehow. You mention ATi drivers, how did you install them ?

---

### Post by dbbolton on 2008-07-21
> **HymnToLife said:**
> Maybe your X configuration got screwed somehow. You mention ATi drivers, how did you install them ?
I tried running X without my xorg.conf at the advice of someone on the Debian forums ( [http://forums.debian.net/viewtopic.php?t=28910](http://forums.debian.net/viewtopic.php?t=28910) ) . So, I don't think there was anything wrong with the conf, but even if there was, there were other problems too.

I installed the 'ati' driver from the package 'xserver-xorg-video-ati', but I also tried the 'vesa' driver.

---

