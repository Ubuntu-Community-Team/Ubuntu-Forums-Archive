---
title: "Blew up Gnome by chrooting USB drive"
date: 2009-11-24
forum: Desktop Environments
---

### Post by kayve on 2009-11-24
I have three SATA hard drives (HDs) for my Gateway MD7818u laptop.  Right now I have used a screwdriver (somebody told me once to mount my disk "with a screwdriver") to return the original Microsoft HD because this is the only windowing system I have for this computer now.  

I have been taking too many pictures:

[http://www.monkeyview.net/id/965/fsck/gentoo/](http://www.monkeyview.net/id/965/fsck/gentoo/)

but you can click on thumbnails to get a better view.. I can get bare X on the Gentoo HD, at least last time I tried:

[http://www.monkeyview.net/id/965/fsck/gentoo/PB230095.vhtml](http://www.monkeyview.net/id/965/fsck/gentoo/PB230095.vhtml)

so If somebody suggests a config file to provide to the forum I can email it to myself via pine and get it here.

Somebody told me to do this (there is a typo it should be "/etc/init.d/xdm stop" )

[http://www.monkeyview.net/id/965/fsck/gentoo/PB230078.vhtml](http://www.monkeyview.net/id/965/fsck/gentoo/PB230078.vhtml)

That's how I get that X.  I had to blow this picture up:

[http://www.monkeyview.net/id/965/fsck/gentoo/PB240006.vhtml](http://www.monkeyview.net/id/965/fsck/gentoo/PB240006.vhtml)

to get the information about null.  It also talks about /var/log/Xorg.0.log I guess I should see what that is and email it to myself.  I tried booting up with the USB plugged in, not something I normally do:

[http://www.monkeyview.net/id/965/fsck/gentoo/PB24000401.vhtml](http://www.monkeyview.net/id/965/fsck/gentoo/PB24000401.vhtml)

Oh well.

---

### Post by Vadi on 2009-11-25
Is that on Ubuntu?

---

### Post by kayve on 2009-11-25
> **Vadi said:**
> Is that on Ubuntu?

I have posted 1980 photos of the "shenanigans" I have been pulling with two laptops and six hard drives over the past few years here:

[http://www.monkeyview.net/id/965/fsck/index.vhtml](http://www.monkeyview.net/id/965/fsck/index.vhtml)

It is of course absurd of me to expect anyone out of their good graces view them all, but at the same time, it may be absurd of me to take advice from someone whose inadequate understanding of my system ends up doing more harm than good.

OK. That was overly melodramatic.

Nestled in the second most recent "Album" of visual documentation of my activities are 165 photographs of my three hard drives (HDs) and I have been careful to have some nice closeups to show the multiple logos I have affixed to them to show the respective distro contained therein.   The original HD that came with the system has Microsoft logos affixed, and the two HDs purchased subsequently have Ubuntu, and Gentoo logos to designate a similar dedication.

[http://www.monkeyview.net/id/965/fsck/gentoo/index.vhtml](http://www.monkeyview.net/id/965/fsck/gentoo/index.vhtml)

Two Linux HDs side by side:

[http://www.monkeyview.net/id/965/fsck/gentoo/PB210338.vhtml](http://www.monkeyview.net/id/965/fsck/gentoo/PB210338.vhtml)

swapping into the "master slot."

[http://www.monkeyview.net/id/965/fsck/gentoo/PB210347.vhtml](http://www.monkeyview.net/id/965/fsck/gentoo/PB210347.vhtml)

The monkeyview site has somewhat convenient navigation between photos.. clicking on links in the upper right hand corner brings you out, from a single closeup view of a picture that you can actually read command lines in many of the photos, such as the two most recently provided can give way to the hierarchical structure outward to "Efforts to Run Gentoo Linux" which is the third most recent URL given above is attainable by clicking on that link.   This view shows thumbnails of all 165 photos. 

What I have been doing, is utilizing this external 2.5" HD enclosure:

[http://www.monkeyview.net/id/965/fsck/gentoo/PB210414.vhtml](http://www.monkeyview.net/id/965/fsck/gentoo/PB210414.vhtml)

to bring a Gentoo Linux up using the convenience of my Ubuntu Gnome terminals to mount the disk.  When a disk is in the "master slot" it is known as "/dev/sda" and when it is in the USB device it is known as "/dev/sdb"  I have been repeatedly swapping all three disks, now running Microsoft because it is the only GUI system I currently have operational.  

Pictures such as this:

[http://www.monkeyview.net/id/965/fsck/gentoo/PB210359.vhtml](http://www.monkeyview.net/id/965/fsck/gentoo/PB210359.vhtml)

show the GEntoo system taking over the laptop, inserted into the "master slot" (if this term is foreign, please at least take a look at that one picture of what I am talking about given above).  

Here is a picture of Gentoo running what I call "bare X" 

[http://www.monkeyview.net/id/965/fsck/gentoo/PB210362.vhtml](http://www.monkeyview.net/id/965/fsck/gentoo/PB210362.vhtml)

Gentoo was giving me pretty Gnome flowers:

[http://www.monkeyview.net/id/965/fsck/gentoo/PB22001801.vhtml](http://www.monkeyview.net/id/965/fsck/gentoo/PB22001801.vhtml)

but when I logged in, the session lasted for less than 10 seconds with this dialog box:

[http://www.monkeyview.net/id/965/fsck/gentoo/PB230073.vhtml](http://www.monkeyview.net/id/965/fsck/gentoo/PB230073.vhtml)

I ran some Gentoo "emerges" (the equivalent of apt-get install) on the "bare X" 

[http://www.monkeyview.net/id/965/fsck/gentoo/PB240114.vhtml](http://www.monkeyview.net/id/965/fsck/gentoo/PB240114.vhtml)

Eventually, to my horror, these shenaningans have affected Ubuntu, and I have created a new MonkeyView "Album" called "No X disaster Nov 25, 2009" dedicated to these new developments:

[http://www.monkeyview.net/id/965/fsck/nox/index.vhtml](http://www.monkeyview.net/id/965/fsck/nox/index.vhtml)

Here, instead of offering me the Gnome GUI startup login, I am beset with a classic character-based terminal logind with the Ubuntu disk in the "master slot."

[http://www.monkeyview.net/id/965/fsck/nox/PB24000201.vhtml](http://www.monkeyview.net/id/965/fsck/nox/PB24000201.vhtml)

I believe this photo is of Gentoo running the machine, telling me it needs to fsck:

[http://www.monkeyview.net/id/965/fsck/nox/PB24000202.vhtml](http://www.monkeyview.net/id/965/fsck/nox/PB24000202.vhtml)

Ubuntu clearly in charge here:

[http://www.monkeyview.net/id/965/fsck/nox/PB240017.vhtml](http://www.monkeyview.net/id/965/fsck/nox/PB240017.vhtml)

Here, I am presented with a Gentoo controlled machine that allows no log ins:

[http://www.monkeyview.net/id/965/fsck/nox/PB240015.vhtml](http://www.monkeyview.net/id/965/fsck/nox/PB240015.vhtml)

Here I have discovered why:

[http://www.monkeyview.net/id/965/fsck/nox/PB240027.vhtml](http://www.monkeyview.net/id/965/fsck/nox/PB240027.vhtml)

In the latest link, I am sure that Ubuntu is in the master slot, only offering me a character based full screen terminal.  I have mounted the Gentoo disk in the enclosure and discovered that the /etc/passwd file for Gentoo has only one entry, that for gdm. This clearly explains how to get login priviledges back for Gentoo, I guess.. I'll have to look that up.. somebody told me about vipw I have a feeling I might have to do that again, unless it is a FreeBSD specific utility. 

ANyway.. I guess I can't expect you to know much about Gentoo.. I am hoping you can help me restore my Ubuntu Gnome, however.

> **vadi said:**
> is that on ubuntu?

yes

---

