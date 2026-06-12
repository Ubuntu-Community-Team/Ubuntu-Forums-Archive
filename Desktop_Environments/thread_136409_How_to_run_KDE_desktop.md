---
title: "How to run KDE desktop?"
date: 2006-02-25
forum: Desktop Environments
---

### Post by lakelovers on 2006-02-25
I have Breezy 5.10 running and I have downloaded/installed all but a few unwanted kde programs with Synaptic. I can run those programs but I believe they are being run in GNOME. My question is: Do a need to download/install Kubuntu to use the kde desktop/gui?

---

### Post by Xian on 2006-02-25
[QUOTE=lakelovers]Do a need to download/install Kubuntu to use the kde desktop/gui?[/QUOTE]

That is unnecessary. You can use the Debian method:
$ sudo apt-get install kde

---

### Post by shams2 on 2006-02-25
to install kde desktop do:
sudo apt-get install kubuntu-desktop

---

### Post by Xian on 2006-02-25
That will install a kubuntu envrionment, but as mentioned it is not necessary in order to get a kde desktop. In short, you do not have to download anything to do with Kubuntu in order to use kde normally. Just a matter of choice.

Minimal KDE desktop:
$ sudo apt-get install kde-core

Full KDE desktop:
$ sudo apt-get install kde

Kubuntu KDE desktop:
$ sudo apt-get install kubuntu-desktop

The "Whole Nine Yards":
$ sudo aptitude install kubuntu-desktop kde

---

### Post by abhaysahai on 2006-02-26
its like 
sudo apt-get install kde will install full KDE ( highly bloated, eg includes kdegames, kdemultimedia etc)
kubuntu-desktop will install too many kubuntu specific things like amarok. 
Both results in some extra things over the other and in turn bloat the DE. 
just to have a KDE experience a minimal KDE would be just fine. 
you can then install the required kde packages.

---

### Post by tadashi on 2006-02-26
If you have downloaded the KDE desktop/environment from the package manager then reboot and when logging in select KDE under session type.  The KDE desktop loads everything.  If you are short of space just load the base or core KDE and then select the apps you want.

---

### Post by lakelovers on 2006-02-26
Thanks all. I have KDE desktop up and running. I suppose this has been asked but I'm wondering which is the most popular desktop KDE or Gnome?

---

### Post by aysiu on 2006-02-26
[QUOTE=lakelovers]Thanks all. I have KDE desktop up and running. I suppose this has been asked but I'm wondering which is the most popular desktop KDE or Gnome?[/QUOTE] On these forums, Gnome. Anywhere else in Linux, KDE.

---

### Post by tadashi on 2006-02-27
[QUOTE=lakelovers]Thanks all. I have KDE desktop up and running. I suppose this has been asked but I'm wondering which is the most popular desktop KDE or Gnome?[/QUOTE]

<listens for the opening of a can of worms> hehehe Personally, I like KDE for the eye candy/customization of the desktop.  I have always used KDE since it was default on most of the other distros.  Although, I had both Ubuntu and Kubuntu and did not see much of a difference in operation other than a few extra options for looks.

---

