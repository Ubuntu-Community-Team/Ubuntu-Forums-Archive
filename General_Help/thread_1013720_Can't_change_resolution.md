---
title: "Can't change resolution"
date: 2008-12-17
forum: General Help
---

### Post by DrMrHorse on 2008-12-17
Noob here.

I've just installed Kubuntu 8.04 using wubi, using the safe graphics mode due to freezing when it got to desktop (before ubiquity.)  Kubuntu is running, but only in 600X400, which is pretty much unusable.

It seems like it might be related to the video card.  The card is an Intel 865G.  

I have tried editing the xorg.conf but there aren't any resolution settings there now under device just "vesa" for the driver. 

I installed 915resolution and tried to change the settings at etc/default/915resolution.  I was able to edit the file but the last step is the xorg.conf thing.

Can someone help or send me in the right direction?

---

### Post by Jammanuser on 2008-12-17
> **DrMrHorse said:**
> Noob here.

I've just installed Kubuntu 8.04 using wubi, using the safe graphics mode due to freezing when it got to desktop (before ubiquity.)  Kubuntu is running, but only in 600X400, which is pretty much unusable.

It seems like it might be related to the video card.  The card is an Intel 865G.  

I have tried editing the xorg.conf but there aren't any resolution settings there now under device just "vesa" for the driver. 

I installed 915resolution and tried to change the settings at etc/default/915resolution.  I was able to edit the file but the last step is the xorg.conf thing.

Can someone help or send me in the right direction?

hmm...could be a bug in the 8.04 release of Wubi! ;) I would suggest using the latest release: 8.10

You will find it [HERE]("http://www.wubi-installer.org/")

Cheers! ):P

Jam Man

:guitar:

---

### Post by DrMrHorse on 2008-12-17
Thank you for your suggestion sir.

As great minds think alike, I upgraded to 8.10 this morning and found the same problem, and a new one: the text size was so small that I couldn't read it.  In light of this, I uninstalled and reinstalled Kubuntu 8.04, which seems more to my taste anyway.

Any other possibilities?  I really like my friend's Kubuntu and I'd love to get it running swanky.

---

### Post by DrMrHorse on 2008-12-17
This just in:
It seems that I have no audio either.  I'm getting into deeper water the more I look.  Is it worth it?

---

### Post by Jammanuser on 2008-12-17
> **DrMrHorse said:**
> This just in:
It seems that I have no audio either.  I'm getting into deeper water the more I look.  Is it worth it?

Personally, i think u would be better off doing a real install of Ubuntu (or Kubuntu, Xubuntu, etc.), instead of using Wubi. This can be done by partitioning ur hard drive, with a program like Gparted on ur LiveCD (System>Administration>partition editor), and then installing Ubuntu (or whatever distro) on the newly created partition. This (in my mind, at least...others might disagree) would probably be your best bet.

However, before doing that, u might want to check first that Ubuntu (or other distro) is combatible with ur system's hardware... ;)

Cheers! ):P

Jam man

:guitar:

---

### Post by ago on 2008-12-19
Video / audio / networking issues are unrelated to the use of Wubi. You would have the same issues in a real installation. Check whether a particular driver is required. For audio it is sometime a configuration issue.

---

