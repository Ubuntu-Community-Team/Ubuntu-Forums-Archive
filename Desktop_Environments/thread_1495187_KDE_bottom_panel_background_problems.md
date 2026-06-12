---
title: "KDE bottom panel background problems"
date: 2010-05-27
forum: Desktop Environments
---

### Post by rhinert on 2010-05-27
I've been installing and reinstalling 10.04 Kubuntu for the better part of 10 days, and each install seems to have problems the the bottom panel background.  Sometimes right away, sometimes after a few boots, the bottom panel will flip over to a solid black color.

I go into K-menu -> settings -> system settings -> advanced -> desktop theme details and "panel background" appears to be set for a light color "air" background.  I have to play with different selections for the panel background until the "apply" button goes active.  I then press apply and the panel will turn a light color again.  Sometimes it will stay a light color for a few boots, sometimes it won't.  In the end, it always wants to revert to a black panel.

Is this a bug or am I doing something wrong?

---

### Post by shaka_zulu on 2010-05-27
That is probably a bug because i had a similar problem but after a few updates it disappeared. Did you make updates? Did you checked all the update options in you Synaptic or Adept manager?

---

### Post by rhinert on 2010-05-27
> **shaka_zulu said:**
> That is probably a bug because i had a similar problem but after a few updates it disappeared. Did you make updates? Did you checked all the update options in you Synaptic or Adept manager?



I've had all the updates available now.  I'll keep a watch on it.  Thanks ......

---

### Post by rhinert on 2010-05-27
Shutdown the machine for a bit and just booted up -- the bottom panel flipped to black again.  I guess this hasn't been addressed yet.......

---

### Post by linuxnoob420 on 2010-05-28
do you have desktop effects on just wondering

---

### Post by shaka_zulu on 2010-05-28
If you have Compiz turned on try to disable it! Maybe this will work.

---

### Post by rhinert on 2010-05-28
> **linuxnoob420 said:**
> do you have desktop effects on just wondering


Yup ... and the Nvidia proprietary driver.  I'm turning off desktop effects as we speak.  

[edit added] Oops.  I thought I had desktop effects on, but it's off.  I tried to turn it on yesterday but I did not have the Nvidia card set for hardware acceleration so KDE complained it could not turn on desktop effects at that time.

---

### Post by rhinert on 2010-05-28
> **shaka_zulu said:**
> If you have Compiz turned on try to disable it! Maybe this will work.



What is compiz?  How do I tell if it's on or off?  Thanks.

---

### Post by shaka_zulu on 2010-05-28
What is your KDE theme at the moment? Return your theme to default one - Air.
Compiz is a windows manager like Kwin but it is not native KDE windows manager. Mostly it is making problems with KDE.

---

### Post by shaka_zulu on 2010-05-28
What nVidia drivers do you have?

---

### Post by rhinert on 2010-05-28
The theme was custom -- now set to air.  The Nvidia proprietary vidio drivers are identified as "current version".  No version number given.

---

### Post by flan_suse on 2010-07-23
This is a known bug with KDE 4.4.x, which is fixed in 4.5, from what I've heard. (The fix might even have been backported to 4.4.5.)

Regardless of the video card and driver, you will be affected.

For the time being, this can be used as a temporary fix: [http://kubuntuforums.net/forums/index.php?topic=3110128.0](http://kubuntuforums.net/forums/index.php?topic=3110128.0)

---

