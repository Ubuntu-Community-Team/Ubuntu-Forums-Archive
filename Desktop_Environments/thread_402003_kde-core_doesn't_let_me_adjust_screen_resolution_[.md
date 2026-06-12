---
title: "kde-core doesn't let me adjust screen resolution? [Resolved]"
date: 2007-04-05
forum: Desktop Environments
---

### Post by Storm Rider on 2007-04-05
Hello,

Running Ubuntu Edgy, installed KDE Core which I believe installed all the dependencies needed for a KDE desktop without having to run Kubuntu.  By choice I kept GDM.

The only problem I've found is that when in KDE, I can't see how to adjust the screen resolution.  Can you help?:)

---

### Post by TheWizzard on 2007-04-05
> **Storm Rider said:**
> Hello,

Running Ubuntu Edgy, installed KDE Core which I believe installed all the dependencies needed for a KDE desktop without having to run Kubuntu.  By choice I kept GDM.

The only problem I've found is that when in KDE, I can't see how to adjust the screen resolution.  Can you help?:)
system settings -> hardware -> display

---

### Post by Jucato on 2007-04-05
> **TheWizzard said:**
> system settings -> hardware -> display

He won't have System Settings installed, as he didn't install the default Kubuntu system.

Rather, go to K Control -> Peripherals -> Display.

---

### Post by aysiu on 2007-04-05
I think you're missing a package called *kde-guidance*

Install that. Or if that package doesn't exist (I'm going on memory here), search for it: ```
aptitude search guidance
```

---

### Post by Storm Rider on 2007-04-05
> **aysiu said:**
> I think you're missing a package called *kde-guidance*

Install that. Or if that package doesn't exist (I'm going on memory here), search for it: ```
aptitude search guidance
```

Thanks to you all.  kde-guidance is what solved the problem.:)

---

### Post by TheWizzard on 2007-04-05
> **Jucato said:**
> He won't have System Settings installed, as he didn't install the default Kubuntu system.


oops :oops:

---

### Post by Jucato on 2007-04-05
I think KDE ships with its own Display settings module, which kde-guidance replaces once it's installed. kde-guidance is Kubuntu's home-grown, python-based, control modules.

---

### Post by Stickymaddness on 2007-04-06
> **aysiu said:**
> I think you're missing a package called *kde-guidance*

Install that. 

I had the same problem till I stumbled upon this thread, thanks this helped me too! 

Just out of interest, why don't they include kde-guidance when you install kde? I sat meticulously checking every menu for something that would let me change my screen res, being used to gnomes Pref->Screen Res, and found nothing... Seems a little strange having to download an addition application for something as trivial as changing display modes.....

---

### Post by aysiu on 2007-04-06
> **Stickymaddness said:**
> I had the same problem till I stumbled upon this thread, thanks this helped me too! 

Just out of interest, why don't they include kde-guidance when you install kde? I sat meticulously checking every menu for something that would let me change my screen res, being used to gnomes Pref->Screen Res, and found nothing... Seems a little strange having to download an addition application for something as trivial as changing display modes.....
They include it when you install *kubuntu-desktop* or *kde*, but if you install *kde-core* or *kdebase*, then they won't install it. Those last two are more minimalist approaches to KDE.

---

### Post by Jucato on 2007-04-06
The KDE Guidance modules (kde-guidance), despite its name, is a Kubuntu-only product. It's not part of the main KDE modules. As mentioned by aysiu, kde-core installs only the most basic/minimal KDE apps/utilities, which doesn't include distro-specific utilities. That's why kde-guidance is not installed, and neither is System Settings (KControl is the default KDE control center) nor Adept (the base KDE system doesn't have a package manager).

---

### Post by MamiyaOtaru on 2007-04-13
> **Jucato said:**
> (the base KDE system doesn't have a package manager).

Sure it does: kpackage.

Kpackage has built in stuff for editing repositories, running apt-get update and installing stuff while taking care of dependencies.  It's really not too bad for basic stuff.

---

### Post by Jucato on 2007-04-13
> **MamiyaOtaru said:**
> Sure it does: kpackage.

Kpackage has built in stuff for editing repositories, running apt-get update and installing stuff while taking care of dependencies.  It's really not too bad for basic stuff.

You forget, we are talking about a kde-core installation here. This means that only kdelibs, kdebase, and arts are installed. KPackage is a part of the kdeadmin module, which is not installed by default on a kde-core/base kde installation. It's really a barebones installation.

---

