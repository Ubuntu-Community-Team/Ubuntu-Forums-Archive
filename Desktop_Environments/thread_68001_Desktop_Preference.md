---
title: "Desktop Preference"
date: 2005-09-21
forum: Desktop Environments
---

### Post by robertpratt on 2005-09-21
I've read the posting rules, and I hope I'm obeying them... 

I am thinking about trying Ubuntu, but before I do, I would like to have 2 questions answered.

1.) Using Ubuntu, can I easily install and use KDE for my desktop? Nothing against Gnome, but I just can't make heads or tails out of it. :???: 

2.) Is there an easy-to-install ATI driver available upon Ubuntu installation? I (unfortunately) have an ATI Radeon 9800 Pro AIW and I am using a (particular) release of Linux simply because it offers easy setup of my card. FGLRX drivers are setup upon installation. I've tried installing the ATI drivers from ATI and all the questions it asks me are way over the head of this noob to Linux.  ](*,) 

Thanks for your patient  and thoughtful support. :) 

Robert

---

### Post by Mustard on 2005-09-21
If you want to use KDE, you should install Kubuntu.

---

### Post by psychicdragon on 2005-09-24
If you want to try out Gnome as well as KDE you can install Ubuntu and then later install Kubuntu through apt. Otherwise you can get the Kubuntu iso instead.
```
sudo apt-get install kubuntu-desktop
```
You can get the ati drivers with
```
sudo apt-get install xorg-driver-fglrx
```

---

