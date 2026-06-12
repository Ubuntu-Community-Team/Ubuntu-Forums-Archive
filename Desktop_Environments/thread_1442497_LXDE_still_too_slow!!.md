---
title: "LXDE still too slow?!?!"
date: 2010-03-30
forum: Desktop Environments
---

### Post by Lord.Quackstar on 2010-03-30
I'm a recent convert from Windows XP to Ubuntu on my old desktop machine. I'm just trying to get away from the viruses of XP and see if there is anything light.

Here are some specs: 
CPU - 2.8 GHz Intel Pentium 4
RAM - 256mb <--big killer
Swap - ~1.4 GB. 1.1 GB on separate disk (higher swap priority), 300mb on current disk partition
Video - Integrated Intel 82865G
Disks - 2 IDE's (7200rpm) over IDE

Obviously, It kinda sucks, so I need a lighter environment. With XFCE running a little slow on another old system I have, I'm using LXDE instead, and replacing Firefox with Chrome. However I'm running into weird issues that weren't in XP
1) Only ~70 MB RAM available most of the time...: This is I guess attributed to the way linux handles memory. But what swappieness value you all recommend for this system? Many of the guides I see go all over the place. 
2) Abnormally high processor usage: When doing anything in chrome or in synaptic processor usage shoots up. This is weird because on another old system I have that's even worse (Intel Mobile something at 1.5 GHz but with 512mb RAM), chrome doesn't do this. This makes it almost unusable due to the extreme lag. Just opening up a webpage makes CPU jump to 100% or typing something into the address bar.
3) Looks like disk thrashing: The activity light is usually solidly on most of the time. I can hear both disks (their pretty loud) seeking frequently. 

So this where I hope the community could help me. This is extreamly slow and almost unusable unless I'm reading a book while doing anything. Should I change to another desktop environment? Should I increase/decrease my swap size? Should I switch browsers (note that I use  Flash heavily)? Or should I just stick with XP (I'm considering this because it feels like I'm downgrading)? What can I do?

And before you say anything, no, adding RAM nor buying another computer are options.

---

### Post by kerry_s on 2010-03-30
so you inslalled on top of ubuntu gnome?
if so i would recommend a fresh install with only lxde.
[http://people.ubuntu.com/%7Egilir/lubuntu-lucid-beta1.iso](http://people.ubuntu.com/%7Egilir/lubuntu-lucid-beta1.iso)

if its still to heavy i recommend you grab debian net installer & install the lxde desktop in the advanced menu. the net installer can install all desktop versions.
lenny:
[http://cdimage.debian.org/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-businesscard.iso)
squeeze:
[http://cdimage.debian.org/cdimage/squeeze_di_alpha1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/squeeze_di_alpha1/i386/iso-cd/debian-testing-i386-businesscard.iso)

i have debian lenny lxde on 450mhz 256mb ram, the older programs work better for the old laptop.

and you know what "get more ram!" :lolflag:
(i just had to, couldn't resist)

---

### Post by Lord.Quackstar on 2010-03-30
I took an Xubuntu and installed LXDE on top of it. 

You link to some debian ISO's, and that worries me. Will I still have access to the Ubuntu repo's? And whats the difference between lenny and squeeze?

---

### Post by Temposs on 2010-03-30
kerry_s is recommending Debian to you. If you want Ubuntu, then you need to install Lubuntu. There are some download links if you scroll down a bit on this page: [http://lubuntu.net/](http://lubuntu.net/)

Note that Lubuntu does not have a stable release yet. If you want a true taste of how LXDE will run on Ubuntu, then wait until the 10.04 release at the end of April. There will then be an official stable Lubuntu release.

---

### Post by Rodney9 on 2010-03-30
Try this - 

[http://www.linuxmint.com/rel_helena_fluxbox.php](http://www.linuxmint.com/rel_helena_fluxbox.php)

it looks and works beautifully.

> This is the Fluxbox Community Edition for Linux Mint 8, codename Helena. This release has been built with the emphasis on a lightweight and yet fully functional desktop centered on the Fluxbox window manager. Even though we strive to provide out-of-the-box readiness for all your hardware and common computing tasks, Linux Mint Fluxbox CE is easily configurable to run on lower-spec hardware with the tools needed for doing so readily available.

> System requirements

    * x86 processor
    * 256 MB of system memory (RAM)
    * 3 GB of disk space for installation
    * Graphics card capable of 800x600 resolution
    * CD-ROM drive or USB port


---

### Post by kerry_s on 2010-03-30
> **Lord.Quackstar said:**
> I took an Xubuntu and installed LXDE on top of it. 

You link to some debian ISO's, and that worries me. Will I still have access to the Ubuntu repo's? And whats the difference between lenny and squeeze?

the top link is lubuntu, that's what i'm using on my nettop. debian runs lighter then ubuntu, so i threw those in for good measure.

start with lubuntu see how that runs:
[http://people.ubuntu.com/%7Egilir/lubuntu-lucid-beta1.iso](http://people.ubuntu.com/%7Egilir/lubuntu-lucid-beta1.iso)

if it's still slow then try the debian.
squeeze will be more up to date, so it's heavier then lenny.

---

### Post by Lord.Quackstar on 2010-03-30
> **Rodney9 said:**
> Try this - 

[http://www.linuxmint.com/rel_helena_fluxbox.php](http://www.linuxmint.com/rel_helena_fluxbox.php)

it looks and works beautifully.

I think I'm going to try this first since I have time to burn. Also going down the chain (at least to me) is alot less scary then going up the chain. 

> **kerry_s said:**
> the top link is lubuntu, that's what i'm using on my nettop. debian runs lighter then ubuntu, so i threw those in for good measure.

start with lubuntu see how that runs:
[http://people.ubuntu.com/%7Egilir/lubuntu-lucid-beta1.iso](http://people.ubuntu.com/%7Egilir/lubuntu-lucid-beta1.iso)

if it's still slow then try the debian.
squeeze will be more up to date, so it's heavier then lenny.

Apparently I didn't look hard enough for a premade ISO... thanks for giving me a link. After Mint I'll give squeeze a try since I don't want to be out of date with Lenny.

Thanks all for your advice!!

---

### Post by vger7 on 2010-04-01
I also have a P4 with 256M ram.
Ubuntu (Jaunty) was too slow, Xubuntu, not much better.
So I put LXDE on top of it and it *is definitely faster*.
(I'm using it at this moment).
But the low memory does cause disk trashing and high CPU
usage at times. (Firefox is the main culprit here.)

But please go here and see my post (#9) of things I'm comparing at the moment.
[http://ubuntuforums.org/showthread.php?t=1442874](http://ubuntuforums.org/showthread.php?t=1442874)
It hope you find it useful.

---

### Post by cascade9 on 2010-04-01
> **kerry_s said:**
> the top link is lubuntu, that's what i'm using on my nettop. debian runs lighter then ubuntu, so i threw those in for good measure.

start with lubuntu see how that runs:
[http://people.ubuntu.com/%7Egilir/lubuntu-lucid-beta1.iso](http://people.ubuntu.com/%7Egilir/lubuntu-lucid-beta1.iso)

if it's still slow then try the debian.
squeeze will be more up to date, so it's heavier then lenny.

I've found squeeze to be pretty much teh same as lenny on low memory/old CPU computers (I havent realy gone under 256MB, but I've got more RAM sticks than I know what to do with...but much, much older CPUs than a P4 .2.8).

I sort-of agree on debian vs ubuntu. Eg xubuntu is a RAM hog compared to Debian Xfce. Using a minimal install on xubuntu brings it down to alomst the same RAM usage as Debian.

---

### Post by SeePU on 2010-04-06
Is Xubuntu or Xfce installed on Ubuntu going to be any good?   I hope not a ram hog.

I have tried LXDE in Debian and it's a piece of crap!

Bug city!!!

I install Synaptic but it is placed into the menu three times.  

I checked the LXDE forum and it seems like no one uses this DE.  I doubt the devs of this DE really give a crap or are doing much to fix bugs.

At least, xfce seems more organized and they have more of a history.

I think LXDE has a long way to go before they will be considered a suitable low resource DE.  It was so promising at first, such a disappointment.

---

### Post by kerry_s on 2010-04-06
> **SeePU said:**
> Is Xubuntu or Xfce installed on Ubuntu going to be any good?   I hope not a ram hog.

I have tried LXDE in Debian and it's a piece of crap!

Bug city!!!

I install Synaptic but it is placed into the menu three times.  

I checked the LXDE forum and it seems like no one uses this DE.  I doubt the devs of this DE really give a crap or are doing much to fix bugs.

At least, xfce seems more organized and they have more of a history.

I think LXDE has a long way to go before they will be considered a suitable low resource DE.  It was so promising at first, such a disappointment.

lxde is still the new kid on the block.
xfce4 is still good too.

linux is a user os, it can be what ever you want, all you have to do is be willing to do the work to make it do what you want.
nothing is just right when first installed, it always has to be tweaked/changed/fixed in some way or another, that's just how it is.

i mix from all the other de's & use what works for me. you can mix and still be light. my startup ram use is only 83mb & usually hovers around 200mb through out the day.
i personally love xfce4-panel, cause it's got great applets & you can use gnome applets to. 
so i use it in lxde, it's the top panel in the pic.

---

