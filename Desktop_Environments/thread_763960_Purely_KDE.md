---
title: "Purely KDE"
date: 2008-04-23
forum: Desktop Environments
---

### Post by curtiswtaylorjr on 2008-04-23
I want a system that is solely a KDE default install on top of Ubuntu. What I mean is an install that doesn't come with the 3rd party apps (ex. open office or thunderbird). Instead having Koffice, Kontact, Korganizer, and so on. I feel that this is what KDE is meant to be and the KDE are also pretty good IMHO.

---

### Post by justin whitaker on 2008-04-23
> **curtiswtaylorjr said:**
> I want a system that is solely a KDE default install on top of Ubuntu. What I mean is an install that doesn't come with the 3rd party apps (ex. open office or thunderbird). Instead having Koffice, Kontact, Korganizer, and so on. I feel that this is what KDE is meant to be and the KDE are also pretty good IMHO.

Grab an alternate install or a server ISO. Install a command line only system. Use aptitude to install KDE Base, KDE Office, etc.

---

### Post by TenPlus1 on 2008-04-23
Install a basic Ubuntu Server then do:

sudo apt-get install kdesktop

and that should give you a very basic kde installation...

---

### Post by curtiswtaylorjr on 2008-04-23
What is the difference between the KDE and Kdesktop packages.

---

### Post by benerivo on 2008-04-23
The kde package is only kde apps, but it is a big download full of programs you'll never use like a chemistry utility, some basic point and click game, or something like that. There is no package called kdesktop. If you want pure kde, then kubuntu-desktop will only install kde apps. You will still have open office in the main menu, but there is nothing you can do about that unless you manually remove them from the menu -- but that is only a cosmetic change.

EDIT  -Sorry, there is package called kdesktop, but it is very minimal. I don't think it will allow you to log in to a kde desktop. If you want minimal i think i would go for kde-core.

---

### Post by lunarcloud on 2008-07-09
I am a KDE fanatic, and think that koffice 2 is the bees knees, but kopete is horrible, aging, and light years behind Pidgin.

---

### Post by ChompTheMan on 2008-07-09
I recommend installing a command line system with the alternate cd, then installing *xorg*, *kde-core*, and *kdm*.  This will give you a minimal, but functional, KDE.  You can then proceed to install whatever apps you prefer, while having a KDE more closer to the original KDE as opposed to Kubuntu's modified version of the KDE(why hide Kcontrol?).

---

