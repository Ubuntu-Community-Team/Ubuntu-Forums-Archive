---
title: "Help for migrating with HP tx2517ca"
date: 2009-04-28
forum: General Help
---

### Post by diosdiablo on 2009-04-28
hi everyone

I'm planning to migrate from vista to ubuntu, but i would just want to know first if it's possible to keep all the hardware of my laptop working.
I have the HP tx2517ca, and it has a lot of things such as touch screen, fingerprint reader, lightscribe dvd drive, webcam, remote control... etc.
where can I find all compatible drivers so I can change OS without any trouble??

Thanks!!

---

### Post by Favux on 2009-04-28
Hi diosdiablo,

Lot's of folks with TX2500's have Ubuntu installed so it should be doable.  Finger print reader and remote control might be tough though.

What version of Ubuntu are you planning on installing?

---

### Post by diosdiablo on 2009-05-02
hey favux, thanx for replying!

well, i'm actually new in ubuntu, so i would think to install the 9.10 just because it's the newest or the 8.10 at least, i really don't know the differences yet, so I just want to install the one that can keep my hardware fully functional. I don't remember where, but I read that it was almost all compatible, but couldn't use anything and the main problem now, is that I can't hear any sound...

thanks!!!

---

### Post by Favux on 2009-05-02
Hi diosdiablo,

I'm guessing you mean you don't hear sound on the live CD (which version?).  Don't worry, there is a well known fix to get sound on the TX2500.

Either one, Intrepid and Jaunty should get all your Wacom working.  Jaunty has a few "bugs" with Wacom currently, but we have already found work arounds.

---

### Post by diosdiablo on 2009-05-03
hey favux

well, I'm actually using jaunty with wubi, but also when I tried it with intrepid didn't get sound. Where can I find this fix you tell me??
I'm understanding that I have to install it completelly in order to see all my hardware work, right? would it work if I do it in a partition??

thanks again!

---

### Post by Favux on 2009-05-03
Hi diosdiablo,

I think you're suppose to be able to get most things working with WUBI.  I used for a week or two early on doing the same thing you're doing.  Not long enough to know all the ins and outs.

To get sound working for a TX2500 (at least in Hardy and Intrepid) to the bottom of the file "/etc/modprobe.d/alsa-base" you add the following line:
```
options snd-hda-intel index=0 model=toshiba position_fix=1
```
To edit the file you would use in a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base

```
Since you have to be root when you edit it gksudo (the graphical version of sudo) will do that. It will ask for your password. Gedit is gnome-edit, a graphical editor.  Which is why you use them together.  To determine your soundchip:
```
aplay -l
```
I'm just not sure how you would do that in WUBI.

Here's some information on partitioning:
[https://help.ubuntu.com/8.04/installation-guide/powerpc/partitioning.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/partitioning.html)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by diosdiablo on 2009-05-08
thanks favux!!

my sound is working great now. 
now i've been searching for more posts to find out how to configure at least the tablet, if you have any recommendation i will really appreciate it. maybe as you said, it will be difficult to find somethng on the remote control, and the fingeprint reader, but i'll also try.
I'll also look for the lightscribe dvd-rom

if i can do all that, i won't be needing to do the partition and i can completely change to ubuntu

thanks!

---

### Post by Favux on 2009-05-08
Hi diosdiablo,

Great!  I'm glad sound is working.

So you want to embark on the adventure that is Wacom in Jaunty.  OK.  First be sure you have the specially patched linuxwacom drivers for Jaunty.  In Synaptics Package Manager verify that the 0.8.2-2 linuxwacom packages are installed.  Search "wacom".  You should see that xorg-xserver-input-wacom (the drivers) and wacom-tools are installed.  If not install them.

In the last couple of days we've found out how to get everything working.  The usb driver (wacom.ko) from 0.8.2-2 doesn't work right.  So we compile 0.8.3-3.  Notice we don't install it we just take the 0.8.3-3 wacom.ko and copy it over the 0.8.2-2 wacom.ko.  Otherwise we keep 0.8.2-2.  This link takes you to the linuxwacom compiling HOW TO:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  At the top is Jaunty User's.  Number 1 takes you to the Jaunty HOW TO.  It tells you how to compile 0.8.3-3 and copy its wacom.ko.  Also there is a brand new 10-wacom.fdi that actually works in Jaunty.  When everything is working there is a link on the first page that takes you to the Rotation HOW TO:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)

Good luck!

---

### Post by diosdiablo on 2010-03-18
Hi Favux!

How is it going, is nice talking to you again.

So I have a new problem with my tx2517ca, and is about the not working wireless on Karmic, I guess you already know the problem since apparently lots of people have it as well, but can't find any useful solution...

Any idea??

Thanks a lot again!

---

