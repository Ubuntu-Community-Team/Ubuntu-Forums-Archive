---
title: "Ubuntu lags on my XPS M1530"
date: 2008-04-15
forum: Dell  Ubuntu Support
---

### Post by Lacrimstein on 2008-04-15
I recently got a Dell XPS M1530, specs are in my signature, and Ubuntu is not working as fast as Vista (before I wiped it :lolflag:). In Vista, everything opened up instantly, as soon as I clicked on the icon; In Ubuntu, there is a couple of seconds of pause before anything, even Nautilus or Appearance Manager, starts up - which is unforgivable with my specs. Once the programs start up, they are fast (except Firefox, it has laggy tabs), but I just want Ubuntu to be snappy - because right now it's just as snappy as my old 256MB ram computer. Turning off compiz doesn't make a difference. Any advice? The only solution I am thinking of is to switch to 64bit, but a) I'm out of CD's b) I don't want to reinstall.

---

### Post by tvtech on 2008-04-15
bummer to hear this I'm thinking about buying that one.

---

### Post by Aearenda on 2008-04-15
Have you tried the old hosts file tweak? See step 3 in [http://ubuntuforums.org/showthread.php?t=712625](http://ubuntuforums.org/showthread.php?t=712625).

---

### Post by notwen on 2008-04-16
Open a terminal and run top to see what's eating possible CPU/memory and slowing down system performance.

---

### Post by Lacrimstein on 2008-04-16
I tried hostfile redirection, no noticeable performance boost though. And my top output is fine, with xorg taking up the most resources - 4% of cpu and 1.8% of ram, so this isn't the problem.

---

### Post by Aearenda on 2008-04-16
Try reducing to 3 Gb RAM (or even 2Gb) - just wondering, having seen [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/141439](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/141439) - I know the video driver is different, but worth trying I think. Kernel parameter mem=3G at boot time.

---

### Post by Lacrimstein on 2008-04-17
Unfortunately that did absolutely nothing either...:(

---

### Post by Aearenda on 2008-04-17
Hmmmm - does your disk drive make any odd noises - is it spinning down very often, so that each app start triggers a spinup? See this thread: [http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

If not, then I'm clutching at straws now... 
1) is the lag present if you start the app from the command line instead of the menu?
2) Does the lag persist on the second start of the same app?
3) Does it behave the same with all networking disabled?
4) Anything odd to do with disks in /var/log/syslog? (I can't define 'odd', it's always gut feel for me!)
5) Is there anything unusual about your Ubuntu installation? eg no swap partition, multiple partitions, unusual filesystem types, extra software installed, moon in the wrong quarter?

---

### Post by siul0_0 on 2008-04-18
I don't have any problems running with COMPIZ-FUSION, AVANT-WINDOWS AND DESKLETS; strangely my specs are a bit less...

XPS 1530. 3G Ram 2.4 dual pro 250 HD 54k

---

### Post by sdennie on 2008-04-18
When you run top are you seeing a high values of %wa at the top of the screen?  It's possible that some app is beating on the disk but using very little CPU.  That can drastically slow things down even with a 7200rpm disk.

If not:

I think Ubuntu in general opens equivalent apps a bit slower than Windows when you first open the app (but, after that it should be lightning fast) because I think it probably preloads a ton of common dlls/exes so stuff is already cached off the disk before you even need it.  Ubuntu does this as well but, not nearly as aggressively.

If apps are starting fast the second time they are started, you could be seeing this.  It may be possible to prefill the disk cache at login or boot time (or even on app load but in a more efficient manner than normal) using readahead but, I've never tried this and can't say how useful it is.  [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651) looks like a fantastic starting place and, I may even try it out myself.

---

### Post by Lacrimstein on 2008-04-19
Well, I can't pinpoint the problem still... I guess I'll just install 64bit Hardy when it comes out (Betas take the excitement out of waiting) and see how it goes

---

### Post by blekos on 2008-04-21
Sorry to hear that,
maybe trying to install prelink to speed things up.

---

### Post by jespdj on 2008-04-21
What wireless network card do you have, the Intel or the Dell card? The Dell card uses the Broadcom chipset as far as I know, which does not work well with Ubuntu.

64-bit Ubuntu 8.04 RC [works great]("http://jesperdj.pbwiki.com/Ubuntu+on+the+Dell+XPS+M1530") on my XPS M1530.

---

### Post by Lacrimstein on 2008-04-21
I have the Intel 3495ABG card. The driver currently has a bug that makes the card unusable. The workaround for it is to use the noapic kernel parameter. Turning the card off and removing noapic from menu.lst doesn't speed it up. Also I am starting to think this is a problem with the graphics driver: [http://ubuntuforums.org/showthread.php?t=747294](http://ubuntuforums.org/showthread.php?t=747294) I know I have a different card, but the restricted driver is the same, I believe...

---

