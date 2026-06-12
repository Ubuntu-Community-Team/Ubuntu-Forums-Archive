---
title: "black screen with white flashing stripes"
date: 2010-07-15
forum: Desktop Environments
---

### Post by 700 on 2010-07-15
on a cold computer randomly appears black screen with white flashing stripes up to half of the screen preceded by a message "checking battery state... [OK]".
- ubuntu 10.04 LTS
- desktop compaq evo d510 sff
- intel 82845G/GL[Brookdale-G]/GE chipset integrated graphic device
keyboard is not active on that black screen, BIOS settings look OK

---

### Post by SteveDee on 2010-07-16
Is this after install of 10.04, or was it working previously and now broken?

---

### Post by 700 on 2010-07-17
this is first install on this machine.

---

### Post by SteveDee on 2010-07-17
2 of my 3 evo D510 usdt computers are running 10.04 and so far I have not completely eliminated problems associated with the Intel chipset. All 3 ran great on 9.04, so I have not bothered to upgrade the 3rd machine.

See this thread: [http://ubuntuforums.org/showthread.php?t=1470930&page=2](http://ubuntuforums.org/showthread.php?t=1470930&page=2)
...along with the Ubuntu info here: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by vikas.sood on 2010-07-17
700, I had a similar problem with my dell inspiron. It turned out that my RAM had crashed. Does this happen every time you boot? or it doesnt boot anymore?

---

### Post by 700 on 2010-07-17
i am writing right now on this computer. this computer is running like an hour right now and several programmes at once - no black screens so far. last time it happened (twice) 2 days ago. its random on a cold computer while working on something. never happened working on blender (rendering), sometimes happened surfing the internet or using toolbars and start-bar.

---

### Post by djinnkeeper on 2010-07-26
I got the flashing screen with white bars while updating, following a fresh install.  After getting it back on and discovering nothing was wrong with the monitor (thank god).. We had it running for over an hour.. (streamed an episode of Star Trek from CBS.com) ..then it very suddenly went black and said "Checking Battery State" and shut down.

I have already posted to the related thread for the battery problem.. but I just thought I'd cross-reference my experience here, because I first noticed the white bars.  Also, it is worth mentioning that this appears to be a chipset problem, rather than having anything to do with the ram or battery.  If you have an Intel 845 chipset on a P4, you're probably susceptible to this problem.  (this of course means that it happens to desktops, too..)

---

### Post by Xaifas on 2010-07-29
I had the exact same problem. My monitor started to flicker and turn off while displaying flashing stripes. I never suspected it is something related to Ubuntu so I to took my monitor to an electrician he changed the image converter went back home used windows for couple of days and when i finally had to work on something booted to ubuntu and it did the exact same thing as last time. I got a WinFast PX9500 GT Nvidia card and using a packard bell lcd monitor....

---

### Post by TimRV on 2010-07-30
> **Xaifas said:**
> I had the exact same problem. My monitor started to flicker and turn off while displaying flashing stripes. I never suspected it is something related to Ubuntu so I to took my monitor to an electrician he changed the image converter went back home used windows for couple of days and when i finally had to work on something booted to ubuntu and it did the exact same thing as last time. I got a WinFast PX9500 GT Nvidia card and using a packard bell lcd monitor....

 I've just upgraded (?) to Lucid from 9.04 and I am seeing exactly the same thing, on an Intel 845 chipset.   It happens when I try to go into the screen saver preferences, but I've been web browsing a couple of times now and the same thing has happened - flashing vertical white lines across the top of the screen, machine unresponsive and have to eb re-booted. It's not the websites. I have re-loaded them after a re-start of Lucid and there are no issues.  This is the first version of Ubuntu that I have found to be unstable. 9.04 was rock-solid, although 9.10 had the same problems as Lucid, for the brief time I had it running before upgrading in the expectation that the new version would fix things.

---

### Post by djinnkeeper on 2010-07-30
Has anyone noticed the problem following any particular keystrokes?  I've seen it happen twice upon striking the backspace key.. (simply during normal use) .. and though I'm 99% sure this is a coincidence, it did *appear* to happen twice.

Going out on a limb here, but is there a combination of shortcut keys to activate hibernation-mode or something?  So far, some people have noticed that it sometimes *appears* to have something to do with their screensaver settings.. just about everyone has confirmed using an 845 chipset.. and we know it's not limited to laptops.  (aside from CMOS, there is no battery to check in a desktop..)

Any other symptoms I am forgetting to mention, that should be kept at the forefront of our reports?

---

### Post by ianozia on 2010-07-31
A friend of mine is having this exact same issue.
Someone even posted the problem on youtube: [http://www.youtube.com/watch?v=Zq-U-fnysIU](http://www.youtube.com/watch?v=Zq-U-fnysIU)

It happens to him, whenever he does a sudo command; he even tried it in tty1, and the same thing happens.

Also, when he installed ubuntu, he installed it from windows (it still boots into grub, and he can duel boot into windows or ubuntu, now, though).

From a quick search, it seems there's a moderate few having this problem, sadly they never find a solution (that is, the topic has no replies).

I hope we can find a solution to this.


EDIT: On a side note, this doesn't just happen in gnome, or in X, as it also happens in the terminal (e.g. tty1, etc).

---

### Post by 700 on 2010-08-05
Confirmation - sudo command and backspace key sensitive problem

---

### Post by Big1984Brother on 2010-08-12
Same problem on a Dell Dimension 2400 w/ a 845 Intel card.  Screen goes black, and vertical white bars appear on a small section in center of the screen. This PC had Ubuntu 8 & 9 before, problem started immediately after upgrading to 10.04.

I guess a lot of other people are having this problem as well...


[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492)

---

### Post by djinnkeeper on 2010-08-13
Honestly, I'm surprised that our Dell (the one in question anyhow) performed as well as it did.  Crashes aside, I have been thoroughly impressed with Xubuntu's performance on the more-or-less stock Dimension 2400.  ..but I knew it was temporary and now I'll be gutting it.  (Yes, I will salvage even the ugliest case)

For anyone that is willing to consider new hardware, but still have to stick to a budget, check out the Atom/ION-based mini-itx boards.  You can get your board w/integrated processor and graphics + memory for about $200 (maybe $250 if you max out the RAM, or buy one of the pricier boards..)  That is all assuming that you have the other parts laying about to cannibalize, but if you can afford that, they are pretty much guaranteed to run circles around our stuffy old P4s.. especially with video.

If you need to save a few more dollars (euros, what have you), skip the ION platform and look at anything sporting an Atom 330.  Alternatively, if you hate integrated processors, the Athlon II X2 has been a wonderful improvement from my old P4.. and it was (by comparison) super cheap.

Good luck fellow crashers.  I hope this bug gets what it deserves - a squashing!

(Oh!  and if you decide to reuse your old Dell cases, remember that their power switches do not comply with the standard pin layout.  Don't get elbow deep in to the refit before assessing your new motherboard's power switch needs!)

---

### Post by carolineictwiki on 2010-08-19
I'm running a 35-seat dual boot lab, and I've got this problem on about 4 computers. 

They are all Compaq Evos, with Intel 845 chips.

They had this problem even while trying to install - and I had to attempt several times or use an alternate CD in order to get a successful installation.

I can induce it with the 'AntSpotlight' screensaver. All the other screensavers are ok, but even in the screensaver preferences window the AntSpotlight sent it straight into the black on bottom, white stripes on top flashing.

Tried backspace and sudo with all of them and they were fine.
I've heard a report that it can happen just during normal work, but haven't seen too much of that.

Other computers in my lab of the same type are not having this problem. 

EDIT: Both Workarounds B and E seem to work - at least they don't crash on the screensaver anymore! [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by Nowarrantee on 2010-08-22
I too have experienced this problem. I am using a Dimension 2400. I was reading some of the older posts and tried a solution offered by aust77. I added a line in as suggested and it works a better. It doesn't seem to crash as much and the black screen with the flashing white stripes is gone, however, you get that battery notification flashing issue and you do need to reboot the computer manually.

---

### Post by rw62827 on 2010-08-22
having same problem when upgrade to 10.4 from 9.10..
screen black with white flashing bars on top..
so>> when is fix coming

---

### Post by KdotJ on 2010-08-22
This problem happens to me occasionally (say 1 in 60 boots). It comes up during loading, but once it reaches GDM it works no problem there on

---

### Post by cutekazuya on 2010-08-23
I had the similar problem when randomly it would go blank with grey stripes. 

If i changed the screensaver to AntSpotLight, it would crash straight away with grey stripes. 

I fixed by switching the "vesa" driver in xorg.conf and it has not crashed on me since 3 weeks now. I can set the AntSpotLight screensaver without any problems aswell now. 

If you look at this thread:

[http://ubuntuforums.org/showthread.php?t=1558917](http://ubuntuforums.org/showthread.php?t=1558917)

I have replied on exactly what i did to fix it.

Hope it helps.

---

### Post by 700 on 2010-12-17
So far no black screens at all with Ubuntu 10.10

---

