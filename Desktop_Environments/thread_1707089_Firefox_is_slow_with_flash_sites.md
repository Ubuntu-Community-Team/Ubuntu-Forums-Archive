---
title: "Firefox is slow with flash sites"
date: 2011-03-14
forum: Desktop Environments
---

### Post by Dr.Paneas on 2011-03-14
Yesterday I've installed Ubuntu 10.10 . Everything is fresh new but my I can feel some lack of speed in the desktop and sometimes if you look really hard on the monitor you can see that screen is trembling a little bit. Not long before, the system freeze up and I had to manually force reboot. 

I think that the root of the evil might be the integrated graphics from Intel Core i5 2500K processor. What's your opinion ?

 [ATTACH]186073[/ATTACH]

---

### Post by Krytarik on 2011-03-14
Concluding from the look of the animation in your screenshot, it seems that you are running Metacity, meaning "System -> Preferences -> Appearance -> Visual Effects -> None". Is that correct? If so, try switching to "Normal" or "Extra", this would enable Compiz.

Also, you may uprade your video driver to the most recent packaged version through Ubuntu-X-Swat's PPA:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Breambutt on 2011-03-14
My "opinion" of flash sites is NoScript.

---

### Post by Krytarik on 2011-03-14
> **Breambutt said:**
> My "opinion" of flash sites is NoScript.
:lolflag:

---

### Post by Dr.Paneas on 2011-03-15
> **Krytarik said:**
> Concluding from the look of the animation in your screenshot, it seems that you are running Metacity, meaning "System -> Preferences -> Appearance -> Visual Effects -> None". Is that correct? If so, try switching to "Normal" or "Extra", this would enable Compiz.

Also, you may uprade your video driver to the most recent packaged version through Ubuntu-X-Swat's PPA:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

Yes man, it seems that I am running Metacity, but how can I check it for sure ?
I've tried to enable compiz with no luck.

[ATTACH]186198[/ATTACH]


I will try the ppa and let you guys know. As far as I am concern there is another ppa, called xorg-edgers. What do you recommended ? Ubuntu stable or Ubuntu bleeding-edge graphics drivers ? btw these are free or proprietary software ?
EDIT: I upgraded my drivers using your x-updates ppa, but nothing happened. I'm still unable to use compiz. :( :(

EDIT2: I have to mention that Firefox is rolling now without the previous lag.  :) So case closed, problem solved ;)

---

### Post by Krytarik on 2011-03-15
Regarding the PPAs: I didn't look so closely on those PPA until now, what drivers they are exactly providing and who offers the most recent version of them. So, let's compare now:

- The Xorg-Edgers are more (and exclusively) involved in building the Open Source Edge driver for ATI/AMD and the "nouveau" driver for Nvidia cards/chips, but don't offer the proprietary "fglrx" driver for ATI/AMD.

- The Ubuntu-X-Swat are mainly involved in building the proprietary drivers for ATI/AMD and Nvidia cards/chips.

- Both offer a more recent driver for your Intel chip than provided by the official repos.

- And all drivers offered by both PPAs which I compared are available in a more recent version in Xorg-Edgers' PPA, at least currently.

Conclusion:
- Ubuntu-X-Swat's PPA for the proprietary ATI/AMD driver
- Xorg-Edgers' PPA for all the rest

Thanks for the inducement to compare those!

---

### Post by Dr.Paneas on 2011-03-16
You 're welcome. Nice informations, exactly what I needed ;)

---

