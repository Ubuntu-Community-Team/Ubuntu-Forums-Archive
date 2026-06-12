---
title: "Would fresh install of nv be erased with a kernel upgrade?"
date: 2012-09-07
forum: Desktop Environments
---

### Post by este.el.paz on 2012-09-07
Folks:

I'm re-posting his thread since the thread that contains a question similar to mine has been marked as solved.  I just recently  installed Xubuntu PPC on my iMac 800 G4 . . .  got "sudo" back working  last night, so I ran "sudo update/upgrade/dist-upgrade" . . . and the  Console came back with one package to upgrade, but three "held back" . .  . one of which was a new "linux-image" kernel.  It was late so I "aborted" the  mission, but a minute or so later "Software Update" flashed a  notification that "7 upgrades are available" . . . which included the  new kernel.  

So, question one: Why the difference in packages between Terminal and  GUI update manager?  And question two: Do I want to install the new  kernel right away because I had to go through a bit of process to  "compile the nv driver" from an older Ubuntu repository.  I've just gone  through in the last year plus 5 installations of various Debian systems on  this computer, the last, straight Wheezy dist-upgrade broke the display  for the umpteenth time with a kernel upgrade that took away fbdev &  nv . . . I'm wondering if my fresh install of nv will be erased with a  kernel upgrade?  Or, sticking with the Terminal's decision, "linux  image" would be "held back" even with "dist-upgrade" . . . would that be  the right decision to get me down the road with less effort figuring the the new kernel would wipe the nv compilation?

Many thanks,

e.e.p.

---

### Post by Epodx64 on 2012-09-07
I don't know if it would wipe out the nv installation but even if you did install the new kernel just don't get rid of the old kernel you can always boot into the old one (from grub) if the new one doesn't work so I'd say go ahead and try whats the worst that could happen? Speaking of PPC installs I have Debian 6.0 installed on a PowerMac G5 with a Nvidia Geforce 5200 FX card the only problem I ever had with it was a phantom tv-output

---

### Post by este.el.paz on 2012-09-07
@Epod:  Thanks for the reply, much appreciated . . . "what's the worst that could happen?" . . . true, it's only time that is being used; guess I'm a bit gun shy as I've got many hours and days flushed in this one already.  But, still the question is still standing in terms of the Terminal sudo update showing the "linux-image" as "held back" . . . but Software Update making it "available" . . . .  From my experience debian updates have not prevented things from breaking in the doing of it, just wondering if the *Buntu flavors are more careful with doing stuff . . . ?????  But, got it on the "you could always boot into the old kernel" . . . thanks for the reminder, I'm still a relative noob in terms of using Linux, although I've now got quite a number of installations done between the iMac, an iBook, and a MBPro that took 5 installs to get LMDE set up right--that last system has been the most trouble free.  But, yes, Debian 6 I did have loaded on the iBook for a few months until Wheezy came out, which is Deb 7, and 7 has been "interesting."  But, even with Deb 6, I couldn't figure out or get help on how to get the display working on the iMac . . . until I got some hints on using "fbdev" as the driver, but then the latest kernel took that one out and I was back in the black as they say . . . .  e.e.p.

---

### Post by Epodx64 on 2012-09-08
> **este.el.paz said:**
> @Epod:  Thanks for the reply, much appreciated . . . "what's the worst that could happen?" . . . true, it's only time that is being used; guess I'm a bit gun shy as I've got many hours and days flushed in this one already.  But, still the question is still standing in terms of the Terminal sudo update showing the "linux-image" as "held back" . . . but Software Update making it "available" . . . .  From my experience debian updates have not prevented things from breaking in the doing of it, just wondering if the *Buntu flavors are more careful with doing stuff . . . ?????  But, got it on the "you could always boot into the old kernel" . . . thanks for the reminder, I'm still a relative noob in terms of using Linux, although I've now got quite a number of installations done between the iMac, an iBook, and a MBPro that took 5 installs to get LMDE set up right--that last system has been the most trouble free.  But, yes, Debian 6 I did have loaded on the iBook for a few months until Wheezy came out, which is Deb 7, and 7 has been "interesting."  But, even with Deb 6, I couldn't figure out or get help on how to get the display working on the iMac . . . until I got some hints on using "fbdev" as the driver, but then the latest kernel took that one out and I was back in the black as they say . . . .  e.e.p.

Installing on an Apple PowerPC is quite a feat. I have Debian 6 installed on a PowerMac G5 DP for some reason ever single install I did on that machine it picked up some phantom t.v. output on the Nvidia card.

---

### Post by este.el.paz on 2012-09-08
> Installing on an Apple PowerPC is quite a feat. I have Debian 6  installed on a PowerMac G5 DP for some reason ever single install I did  on that machine it picked up some phantom t.v. output on the Nvidia  card.

@Epodx64:

It does seem that in either the G5 or G4 iMac Debian seems to "have trouble" with finding the display.  A gentleman on the MintPPC forum, "str8bs" seemed to have come up with some workarounds and possibly got nouveau to work on the G5, but for me on the G4 I couldn't get nouveau to work in various incarnations of Debian . . . even with an xorg.conf file it seemed that eventually or not so eventually the system would . . . I guess "disintegrate" itself would be the best way to put it.  So we'll see how the nv driver holds up . . . this time.  Got LXDE installed last night, seems like it's flashier than the XFCE DE, but seems to max the cpu a lot according to the little cpu graph in the toolbar bottom right.  Otherwise, cool.  No "wake from suspend" . . . right?

e.e.p.

---

### Post by este.el.paz on 2012-09-09
> **este.el.paz said:**
> @Epodx64:

  Otherwise, cool.  No "wake from suspend" . . . right?

e.e.p.

@Epodx64, et al:

In the interest of the conversation, I did summon the courage to run "update/upgrade/dist-upgrade" in LXTerminal, and it again showed the kernel upgrades as "held back" and I went forward on the other upgrades and then it got to something like, "var/log?something, something is locked, are you root?"  and I'm not sure what to do then, I think in Debian we enter "su" and give the root password, but that doesn't seem to work here.  Anyway, I think I ran "sudo -i apt-get upgrade && apt-get dist-upgrade" and it ran that again, first saying kernel held back but then in the next few lines showing the new kernel as ready to be installed, so it must have something to do with being logged in as root that moves it into the queue???  Anyway, it downloaded 50 MB or so and installed the new kernel . . . I rebooted, and hoping that I wouldn't have to hassle the nv compilation process again, it thankfully booted back into the GUI !!!!!!!!  So, the answer is, no, the new kernel did not wipe out the nv driver . . . .  So far, so good, we'll see how far this Xu/Lu system will go on the iMac G4.

e.e.p.

---

