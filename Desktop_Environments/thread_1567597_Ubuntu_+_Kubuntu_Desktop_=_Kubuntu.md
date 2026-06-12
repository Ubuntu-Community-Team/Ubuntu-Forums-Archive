---
title: "Ubuntu + Kubuntu Desktop = Kubuntu ?"
date: 2010-09-04
forum: Desktop Environments
---

### Post by JoyceBabu on 2010-09-04
Hi,

I downloaded and installed Ubuntu 10.10 today. I want to try Kubuntu. Is installing Kubuntu Desktop using

```
sudo aptitude install kubuntu-desktop
```

equivalent to installing Kubuntu from CD?

---

### Post by M93 on 2010-09-04
it will allow u to open kubuntu at log in screen from sessions
yes it is

---

### Post by JoyceBabu on 2010-09-04
Thanks

---

### Post by Silent Warrior on 2010-09-04
That isn't necessarily the truth as I would describe it. Sure, installing kubuntu-desktop will let you log into **KDE** instead of the ordinary Ubuntu's Gnome, but I wouldn't say that magically turns your system from Ubuntu into Kubuntu. They are, after all, one and the same, just different packages installed during OS installation. (And, in the case of Kubuntu vs. Ubuntu, using KDM instead of GDM.) They're all available to every Ubuntu-variant.

*Shrug* I guess it is indeed equivalent to installing Kubuntu fresh, but you'll have to take an active decision if you want KDM instead of GDM. And don't forget the artwork. :)

---

### Post by Nythain on 2010-09-04
Edit: realized i said everything that had already been said, no sense saying it twice

---

### Post by Termaim on 2010-09-06
I've been curious about trying Kubuntu myself... will this break anything on the install, as everything in Ubuntu is based on gnome, or does the kubuntu-desktop install take care of all that for you?

---

### Post by 67GTA on 2010-09-06
It is actually the best of both worlds for me. Kubuntu is built with the Ubuntu base, but uses only 100% KDE. By installing kubuntu-desktop on top of Ubuntu, you get both Gnome and KDE, and can select which one you want at login. You can do the same thing by installing ubuntu-desktop on top of Kubuntu. The only downside is that you have both Gnome/KDE apps in your applications menu, and some of the startup items are duplicated. It doesn't seem to affect boot time though. Just don't forget to install the respective codecs meta package for each.

---

### Post by Termaim on 2010-09-06
As I'm currently doing a fresh install of 10.04 at the moment, may I ask what they are?  :)  It's been a couple years since I did an install and I had actually forgot all about the initial setup with all the codecs and repos...  and if I remember right, even though my /home is a separate partition that's not being formatted, I'll still need to do all of that, correct?

---

### Post by 67GTA on 2010-09-06
Your /home partition only holds your personal application/OS settings. You will have to reinstall your applications that are not default, plus the codecs, plugins, etc. I'm on openSUSE right now, but I believe they are ubuntu-restricted-extras and kubuntu-restricted-extras. You can use aptoncd from the repos to make a backup of your /var/cache/apt folder which will contain a copy of every package you've installed unless you have cleared your apt cache. This will let you reinstall everything without remembering what it is, and downloading them again.

---

### Post by Termaim on 2010-09-06
Awesome, thanks very much.  Hopefully I can get grub working again tonight and then start setting up 10.04 so I can have it working and functional by my day off tomorrow :)  Once I do that, I'm definately going to install the kubuntu desktop and give it a try then.

---

### Post by Nythain on 2010-09-06
KDE 4.5 has been release, and can be obtained in Ubuntu 10.04 Lucid Lynx by adding the Kubuntu backports ppa.
```

sudo add-apt-repository ppa:kubuntu-ppa/backports

```

I highly suggest anyone who's going to be installing Kubuntu or the kubuntu-desktop to use 4.5 as its focus was on a pretty hefty amount of bug fixes and stability.

---

### Post by roddie on 2010-09-20
I read that were was a performance hit if you installed KDE on top of Ubuntu, but since you can choose between them at the start of a session, is that true?

---

### Post by Silent Warrior on 2010-09-20
I'm not sure. There shouldn't be, besides KDE's different system requirements and power management. I can say, though, that I have significantly lower FPS in Flash-content on KDE compared to Gnome...

---

