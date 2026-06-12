---
title: "Trouble getting LIVE CD to boot on E1505"
date: 2007-06-03
forum: Dell  Ubuntu Support
---

### Post by Angelus897 on 2007-06-03
Hey, I've been wanting to install ubuntu on my dell e1505 for quite a bit, but I have run into a problem. When I boot from the cd and try installing (first option), the ubuntu logo starts loading (the black screen), and afterwards I just get a blank dead screen (instead of booting to ubuntu desktop). The cd works absolutely fine on my desktop C2D system, but not on the laptop. Here are the main specs

Core Duo T2300
1GB DDR2-533
Mobility Radeon x1400

Any help is much appreciated, thanks!

---

### Post by Angelus897 on 2007-06-03
Anyone? Anyone? lol. I would really like to switch to Ubuntu on my laptop since everything I use while mobile is available in Ubuntu.

---

### Post by el_poderoso on 2007-06-03
Do a search on ATI video cards on this forum...and feel the "love":(

I booted my live CD on a number of laptops at Best Buy (I was fortunate to get a salesman who was a linux nut). One Compaq model went straight to windows no matter what was done in the BIOS. (Odd, since I am using Compaq now) A Gateway I tried acted much as you describe. One series of Toshibas did everything perfect. I was a Satellite A205-54577 on sale for $749. PERFECTION!  The sales dude even confirmed that the wireless card worked with terminal commands. This guy was WAY TO SMART to be working at Best Buy.

He says (as a Gentoo fan who builds everything from source, yuck) that Toshibas generally work most reliably, BUT, you damn near have to load the live CD and run a few commands [ lspci is one that comes to mind ] to find out what kind of hardware is onboard. As a generality, Intel hardware usually works. ATI and Broadcom, not so much.

Bear in mind that I am a recent convert to Ubuntu, and by no means a guru, but maybe its easier to switch than fight.

With Dells starting at $599 and this bitchin' toshiba going for $749 (1g, duo, 160g HDD, 15.4 screen), maybe its time to consider putting your Inspiron on eBay. Laptops fetch good prices on the used market. Freshmen college students come into the market strong this time of year.

That's what I'm going to do anyway.

---

### Post by Angelus897 on 2007-06-03
^ Yea, I figured that ATI was the problem here. Damn it, I actually wish I went with a Intel IGP and save $100 something bucks. I guess I'll have to swap the card for a 7300/7400 series. Thanks for the help though!

---

### Post by Paul S on 2007-06-04
I was able to install ubuntu with the alternate cd with no problem.  After installing, you need to install xorg-fglrx-driver and edit your /etc/X11/xorg.conf to specify the fglrx driver.  This will get X going.  You'll find a helpful howto on the wiki for installing and configuring ATI cards, if you're not already knowledgable.

The problem with the live cd is a well understood bug that crept in with the final feisty changes, but could not be fixed before the release was made.  For edgy, there was no bug, so the live cd worked fine.  Most likely, gutsy will be ok again.  So, all of us with ATI graphics cards have to use the alternate cd to install feisty.  BTW, the live cd uses the vesa driver, since AMD has failed to allow xorg developer's to release the open source driver.

Actually, if you know your way around linux, you can get the feisty live cd to work by going to a console after the screen goes blank, then editing /etc/X11/xorg.conf to remove all modes from the screen section, and then restart gdm (or kdm for kubuntu users).  This worked a couple times for me, but also failed at least once (had to reboot and start all over) with the live cd .. not sure why.

There are a bunch of threads on this forum about installing feisty on the E1505 with ATI, so you didn't take enough time to search and read.

HTH,

---

