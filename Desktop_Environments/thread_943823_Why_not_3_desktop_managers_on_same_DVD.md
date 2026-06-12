---
title: "Why not 3 desktop managers on same DVD?"
date: 2008-10-10
forum: Desktop Environments
---

### Post by geoffm on 2008-10-10
I've played around with different distributions, and most seem to offer you a choice when you install the distribution between KDE, Gnome and XFCE. Why are they kept seperate and even given a different name in the case of Ubuntu? It even seems to me that a lot of Ubuntu users are not even aware there are versions of Ubuntu with other desktop environments. Wouldn't it be more accessible for the user to be able to try out those DE without downloading 3 times the same OS?

---

### Post by geoffm on 2008-10-10
I've played around with different distributions, and most seem to offer you a choice when you install the distribution between KDE, Gnome and XFCE. Why are they kept seperate and even given a different name in the case of Ubuntu? It even seems to me that a lot of Ubuntu users are not even aware there are versions of Ubuntu with other desktop environments. Wouldn't it be more accessible for the user to be able to try out those DE without downloading 3 times the same OS?

---

### Post by SuperSonic4 on 2008-10-10
Yes, but I think it will be due to space constraints and trouble keeping each one separate. You **could** put the 3 main *buntus onto one disc (but remember kde has both kde3.5.9 and kde4.1.2). The problem I see would be duplication of apps such as having both brasero and k3b for media burning.

The beauty of GNU/Linux is that you can try what you suggest and give the copies to your friends

---

### Post by SunnyRabbiera on 2008-10-10
Well the main reason why Ubuntu hasn't made a full DVD release is that not everyone has a DVD burner and primarily Ubuntu is a gnome distro so of course its going to push gnome first and the others second.
But its just as easy to install XFCE and KDE under ubuntu as it is to burn a CD, thats why the kubuntu and xubuntu desktop packages are there for.

---

### Post by zephyrcat on 2008-10-10
I believe there are three main reasons: (these are just guesses, though, not official)

1. Ubuntu and its derivitives are distributed on a CD (max 700MB) and it would be very hard to fit multiple DEs on the same disc.

2. It would likely be confusing for a new user to be given the option to install what would look like three completely different OSs.

3. It is probably easier to achive a seemless expierience if you are only worrying about one DE, than if you have to write code that works equally well with three DEs.

---

### Post by newlinux on 2008-10-10
I don't know why they aren't all available at install. i do know the differences are a little more than just different DEs (they have different default installed apps) But you  can try the other ubuntus without downloading all 3 isos. You could just do:


```

sudo apt-get install kubuntu-desktop
sudo apt-get install ubuntu-desktop
sudo apt-get install xubuntu-desktop

```
to get the  3 ubuntu based desktop environments from any (x/k)ubuntu install.

---

### Post by Ryadt on 2008-10-10
> **geoffm said:**
> I've played around with different distributions, and most seem to offer you a choice when you install the distribution between KDE, Gnome and XFCE. Why are they kept seperate and even given a different name in the case of Ubuntu? It even seems to me that a lot of Ubuntu users are not even aware there are versions of Ubuntu with other desktop environments. Wouldn't it be more accessible for the user to be able to try out those DE without downloading 3 times the same OS?
You don't have to download the 3 OS to test them out.
You just install their desktop.
e.g. ```
sudo apt-get install kubuntu-desktop
``` will install the kubuntu desktop on your ubuntu desktop. Same goes for xubuntu.

---

### Post by aeiah on 2008-10-10
ubuntu seems to want to promote its self as the distro of choice for the developing world more than most other distributions. it also tries to be very user friendly and simple to get to grips with. if it wants to realistically do these things the distro needs to be small and simple.

have you installed fedora? its on DVD or several CDs. it uses anaconda as its installation program and its easy to install and great to use, but it presents you with a million and one installation choices to configure before going ahead with the install which could be a bit daunting for a first time user, and if you're on a slow connection or only have a cd writer, its a pain in the ***.

---

### Post by Sam on 2008-10-10
You can. Just install the package kubuntu-desktop or xubuntu-desktop.

---

### Post by SuperSonic4 on 2008-10-10
I'm pretty sure the OP knows this but is asking why they are not all on the same live dvd

---

### Post by rishabh on 2008-10-10
Possibly it's just a waste of space to include all the major DEs by default just for people to try out? 
Like, when I download a disc image, I know what DE I want, so I'm saved the trouble of downloading a whole bunch of extra packages.
When I want to try out XFCE, I just install the package. It's only some 100MB, and I have a broadband connection...

---

### Post by overdrank on 2008-10-10
Please do not create multiple threads on the same issue.
Threads merged :)

---

### Post by IanW on 2008-10-11
As I understand things, Ubuntu is Gnome-based and only Gnome based.
Kubuntu & Xubuntu are versions of Ubuntu that have been modified by "The Community" (ie. us),
 to produce alternative DE-based _and therefore unofficial_ OS versions.

---

