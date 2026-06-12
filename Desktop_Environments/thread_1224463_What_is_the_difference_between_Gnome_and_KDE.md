---
title: "What is the difference between Gnome and KDE"
date: 2009-07-27
forum: Desktop Environments
---

### Post by razorboy5 on 2009-07-27
Hi

I've been looking at some of the custom desktops that look VERY amazing.
Many of the GREAT ones i see says it's KDE

so what's the differences between KDE and Gnome

also if i install KDE does that mean i have to give up my Gnome?

and how would i go about installing KDE?

thx

---

### Post by decoherence on 2009-07-27
> **razorboy5 said:**
> Hi

I've been looking at some of the custom desktops that look VERY amazing.
Many of the GREAT ones i see says it's KDE

so what's the differences between KDE and Gnome

also if i install KDE does that mean i have to give up my Gnome?

and how would i go about installing KDE?

thx

GNOME and KDE can happily live side by side.

Installing KDE is as simple as installing the kubuntu-desktop package

```
sudo apt-get install kubuntu-desktop
```

Note, however, that KDE in Jaunty has some issues. You might want to wait until Karmic is released, or use the updated PPAs (launchpad isn't loading for me right now so i can't give you the url)

The difference is the toolkit each one uses for drawing user interface elements. KDE came first but because many people didn't like its license (or its toolkit's license) GNOME was developed.

KDE's license problems were fixed long ago but by that point GNOME was already popular.

UPDATE: the url for the PPA [https://launchpad.net/~kubuntu-ppa/+archive/ppa]("https://launchpad.net/~kubuntu-ppa/+archive/ppa")

---

### Post by razorboy5 on 2009-07-27
alright thx
read some tutorials waiting for replies

installing KDE seems very easy

however how can u delete Gnome when installing KDE?

(i have OCD which will not allow me to have 2 environments at the same time)

---

### Post by decoherence on 2009-07-27
> **razorboy5 said:**
> alright thx
read some tutorials waiting for replies

installing KDE seems very easy

however how can u delete Gnome when installing KDE?

(i have OCD which will not allow me to have 2 environments at the same time)

To remove GNOME, I'd suggest uninstalling the package libgnome2-0. It should clean out most of GNOME, I think.

---

### Post by Raffles10 on 2009-07-27
Before making any significant changes I would recommend trying the kubuntu live cd, it might save you a lot of trouble...;)

---

