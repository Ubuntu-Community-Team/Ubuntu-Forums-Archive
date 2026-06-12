---
title: "Best *buntu distro for saga GIS"
date: 2021-04-26
forum: Education &amp; Science
---

### Post by lorenzopari on 2021-04-26
Hi, I am pretty new to the ubuntu world. I am using SagaGIS on windows to elaborate data for my thesis, but I would like to switch to an ubuntu distro, to do so I would like to start with a bootable USB. My PC is not very powerful, so I think that a light distro could be the best to focus on the elaboration of the data, because I am not interested in many other functions. A few years ago I tried lubuntu, is it a viable option? Do you have any suggestions?

---

### Post by guiverc on 2021-04-26
A number of things will decide what is the best distribution for you

- your intended applications
- your preferred way of working, tastes

and way further down the list is your hardware (particularly RAM, but also cpu & other resources).

My machine is a 2009 dell desktop, and I'm running Lubuntu *development *(*impish* or what will be 21.10 on release in October; its currently identical to 21.04 anyway).

It's light & works really well on my old hardware, however I also have XFCE/Xubuntu & GNOME/Ubuntu desktops installed... They are heavier, slower but still perfectly usable on the machine.  I prefer LXQt (Lubuntu) or XFCE (Xubuntu) as GNOME is a far bit heavier thus a touch slower (but mostly not to my tastes).

I have enough RAM to ignore libraries, and the costs of using one application over another, so I'm happily using a number of GTK apps on this box despite my Lubuntu desktop using Qt5 (ie. I'm wasting RAM). 

On other boxes (a newer thinkpad with only 4GB of ram I'm actually more careful), it's three generations later in CPU, but the smaller amount of RAM makes more difference than CPU.

I tested Lubuntu up to 19.04 using device with as low as 1GB of RAM (*though I'd not want to use such boxes for a lot of tasks, especially if you're trying to multitask*), but have used devices with 2GB to test all releases up to the latest Lubuntu 21.04.  I also test other *flavors* too, but Lubuntu is generally best on resource limited devices (*though if you're using GTK apps my decision on the best would likely alter*).

My point is Lubuntu is great.   But I'd consider your wanted apps first, your tastes, and if you've a RAM limited box, I'd re-consider the desktop choice and make it suit your wanted apps (*if you've >4GB though you can ignore that generally, >6B for sure ignore it*).  Also note:  none of this is new; the library/toolkit detail applies equally in apple mac & windows environments, they just don't mention it & tell you need xxGB of RAM to run something (attempting to simplify the issue down to a number; Qt is used in the windows/mac world too)
[I]
Note:  I have no idea what saga GIS is, so I've ignored that detail sorry, I've also assumed modern Lubuntu using LXQt given the legacy 18.04/LXDE/GTK2 release is days away from EOL[/I]

---

### Post by lorenzopari on 2021-04-27
Thank you very much for your answer. 
I have a laptop with 4 GB of RAM and it is a bit old, so I think that I will try Lubuntu as you have suggested. In the future, I will try other distro to become more familiar to the ubuntu world. You give me a good starting point with your message, thank you.
SagaGIS is a program that I use to elaborate satellite data, it can be very resource consuming, but for my purpose my laptop is luckily enough.

---

