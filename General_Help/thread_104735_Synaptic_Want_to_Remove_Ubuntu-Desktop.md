---
title: "Synaptic Want to Remove Ubuntu-Desktop"
date: 2005-12-16
forum: General Help
---

### Post by Noah0504 on 2005-12-16
I installed the official BitTorrent Client, so I have no need for the Gnome Client.  When I went to remove it, it wants to remove the Ubuntu-Desktop.

---

### Post by aysiu on 2005-12-16
Go ahead and remove ubuntu-desktop. It's not a real package anyway. If you don't believe me, read the description of it in Synaptic.

---

### Post by Noah0504 on 2005-12-16
I believe you, and I thank you for your help. :)

---

### Post by Backharlow on 2007-10-19
I'm experiencing the same scare now. Trying to remove Compiz and it wants to remove ubuntu-deskop as a dependency. This is frightening at first glance. Here is the description:
> The Ubuntu desktop system 
This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.
Okay, that doesn't say that it is a dumby package that can be randomly removed whenever other packages feel like doing so.

---

### Post by aschaetter on 2007-10-29
I'm trying to remove gnome's bittorrent client as well. Hopefully a vet can give us a little help.. *WINK*

---

### Post by Shazaam on 2007-10-29
As aysiu (who IS a "vet" btw) said, removing ubuntu-desktop is safe. Later on if you want to UPGRADE Ubuntu you will need to reinstall it.

---

### Post by Backharlow on 2007-10-30
What I realized upgrading to Gutsy was that reinstalling ubuntu-desktop prior to the upgrade, reinstalled EVERYTHING attached to it including all of the programs I had previously removed individually on Fiesty,such as the gnome bittorrent client aschaetter mentioned. For instance, I don't use wireless, so the Bluetooth service, also, I'm not blind or deaf so the accessibility and speech tools.. all of this stuff I don't want magically reappeared.

---

### Post by scradock on 2007-11-06
So what you're saying is that ubuntu-desktop HAS to be there to install a new version of Ubuntu, but REQUIRES that you accept all these odd programs, each of which is great for someone but which hardly anyone needs all of? That sounds as if someone got dependencies the wrong way round - fine if accessibility program Q requires ubuntu-desktop, but that doesn't mean that it also requires ALL OTHER programs that require ubuntu-desktop.

Can anyone enlighten us poor struggling mortals as to why this apparently bizarre behavior is necessary? If I met it in a commercial OS I would sa "OK, they have to make it to suit everyone, so everything has to be there." But Linux is for people who like to make things work THEIR way - why is it set up so that we can't strip out gnome-pilot if we don't have a Palm Pilot to sync, and so on?

---

### Post by Backharlow on 2007-11-07
> **scradock said:**
> But Linux is for people who like to make things work THEIR way - why is it set up so that we can't strip out gnome-pilot if we don't have a Palm Pilot to sync, and so on?
When I first started using Ubuntu about a year ago it was because A. I knew Linux had matured since the last time I tried, B. Ubuntu had the reputation as being friendly to beginners.
If you take a look at Debian, the main distro Ubuntu draws from, you decide entirely what packages you want and don't want, but you're responsible for your own stability. Whereas Ubuntu is beginner friendly because it's this giant meta-package of stuff from Debian that you probably want. So, I guess it's a trade off; as a beginner most of the time you need to be guided around on a leash, but occasionally the leash can feel restraining.

After reinstalling ubuntu-desktop, then upgrading to Gutsy, I then went back through and uninstalled all the things I didn't want for the second time, and presumably the same thing will occur with the next dist upgrade.

---

### Post by j_dog on 2007-11-07
> **Backharlow said:**
> When I first started using Ubuntu about a year ago it was because A. I knew Linux had matured since the last time I tried, B. Ubuntu had the reputation as being friendly to beginners.
If you take a look at Debian, the main distro Ubuntu draws from, you decide entirely what packages you want and don't want, but you're responsible for your own stability. Whereas Ubuntu is beginner friendly because it's this giant meta-package of stuff from Debian that you probably want. So, I guess it's a trade off; as a beginner most of the time you need to be guided around on a leash, but occasionally the leash can feel restraining.

After reinstalling ubuntu-desktop, then upgrading to Gutsy, I then went back through and uninstalled all the things I didn't want for the second time, and presumably the same thing will occur with the next dist upgrade.



Good explanation !

---

