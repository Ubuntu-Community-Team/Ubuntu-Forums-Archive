---
title: "Display configuration problems"
date: 2011-05-16
forum: Desktop Environments
---

### Post by aphatak on 2011-05-16
I have a wierd problem.  First, my set-up -
[LIST=1]
[*]Intel i5 quad-core CPU
[*]16GB RAM
[*]Two Radeon HD5450 video cards, each with two monitors.
[*]Multi-boot - Windows7, Ubuntu 10.04.2 and Ububtu 10.04.2 (not a typo, the second instance is for experiments)
[*]Both the 10.04's have the proprietary ATI video drivers.
[/LIST]
On the first set-up, everything works beautifully.  All four monitors are alive, and configured with Xinerama as a single large desktop.  In the second Ubuntu 10.04 set-up, I have two problems -
[LIST=1]
[*]The second video card is not recognized - it shows up as an unrecognized card.  Of the two monitors connected to it, only one is detected, with a resolution of 640x480, not the 1920x1080 the first set-up sees.
[*]When I try and switch to the virtual terminal - ctl-alt-F1, I get a blank screen.  The terminal is alive and well - I can log in, and enter commands which are executed.  For example, when I enter 'ls -l > dir.txt', I see a 'dir.txt' file in my home folder; nothing shows on the screen.  And, for my life, I cannot figure out how I got the first set up to work!
[/LIST]
I have tried copying the xorg.conf from the first (working) set-up to the second, but still no joy.  The Grub GFXMODE and GFXPAYLOAD are common to both the set-ups, so that can't be the difference.

Any suggestions?

---

### Post by Krytarik on 2011-05-17
Are both systems running the same version of the proprietary driver?:
```
dpkg -l |grep fglrx
```Is the problem system running it at all?:
```
lshw -c video
```If yes to at least the latter, you may try

[LIST]
[*]reinstalling the driver:
[/LIST]
```

sudo apt-get update
sudo apt-get install --reinstall fglrx
```
[LIST]
[*]upgrading the driver through Ubuntu-X-Swat PPA, it offers more recent drivers than the offical repos:
[/LIST]
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```If you need/want to remove those PPA and downgrade the concerning packages again:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
```Greetings.

---

### Post by aphatak on 2011-05-17
@Krytarik:  Thanks for the pointers.  Will try these out when I get home tonight and post the results.

And this is my strongest reason for switching over from Windows to Linux - your help comes from knowledgeable people who are actually interested in solving your problem, not from a call-center where greenhorns read to you from their ready-made scripts!

---

### Post by Krytarik on 2011-05-17
> **aphatak said:**
> 
And this is my strongest reason for switching over from Windows to Linux - your help comes from knowledgeable people who are actually interested in solving your problem, not from a call-center where greenhorns read to you from their ready-made scripts!
LOL:P Thanks! You are right, Linux in general has a very strong community, and the share of geeks is still relatively high.

---

### Post by aphatak on 2011-05-18
Didn't get the chance to try all the suggestions out yesterday evening.  Planning to do it in the next couple of days - will post the results.

---

### Post by Krytarik on 2011-05-18
> **aphatak said:**
> Didn't get the chance to try all the suggestions out yesterday evening.  Planning to do it in the next couple of days - will post the results.
Yeah, no problem! Take your time.

---

