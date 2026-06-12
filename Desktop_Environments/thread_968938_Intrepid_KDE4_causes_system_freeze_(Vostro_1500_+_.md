---
title: "Intrepid KDE4 causes system freeze (Vostro 1500 + NVidia Drivers)"
date: 2008-11-03
forum: Desktop Environments
---

### Post by goldenboy on 2008-11-03
Hi,

I was pretty excited by the end of last week to get the first (k)ubuntu release with "official" KDE4 support installed. But successful installation was followed by great frustration:

On my Dell Vostro 1500 KDE4 causes the whole system to freeze!! Till now I experienced two different kind of system crashs with KDE4 the first one causes the system to go to Text mode with the whole screen covered by some orange field with blinking signs in them. The other kind of freeze caused the caps lock and scroll lock light of the laptop to blink. In both cases the system does not react to any action (other than pressing the power button for more than 5 seconds...) any more.

While I experienced the second kind of freeze one time only, the first one comes up after round about 15 minutes even if I did nothing more than logging in.


As mentioned in the thread's topic this happens on my Vostro 1500 with the recommended restricted NVidia driver enabled. I already did an "apt-get update && apt-get dist-upgrade" which fetched and installed a new kernel version but did not solve the error :-(

Has anybody similar problems or perhaps even a solution??

Best regards.

---

### Post by goldenboy on 2008-11-03
I forgot to mention that the system for sure does not survive the logout of the user. After pressing the logoff or restart button crash type number one takes place...

---

### Post by goldenboy on 2008-11-08
Actually after switching to OpenSuse for some days. I gave Intrepid a second try and my problem doesn't seem to have anything to do with the nvidia drivers.

I'm currently running a fresh install wo. the restricted drivers enabled and have exactly the same behaviour. Currently I'm fetching KDE3 from the pearsoncomputing repositories (really thanks a lot)

cheers

---

