---
title: "Cinnamon Not in Repos"
date: 2014-05-07
forum: Desktop Environments
---

### Post by amtur_poet on 2014-05-07
After upgrading to Ubuntu 14.04, I noticed that the Cinnamon desktop environment was no longer in the default software repos. I searched around, and found that the repo "ppa:gwendal-lebihan-dev/cinnamon-stable" was supposed to work, but it keep failing to fetch the packages whenever I update. Is there any way to install Cinnamon in 14.04 as of now?

---

### Post by Frogs Hair on 2014-05-07
The PPA only includes 13.10 packages at the moment and last updated 22 weeks ago. You will have to wait for updates.

---

### Post by buzzingrobot on 2014-05-08
"This PPA will not be receiving any new updates." >> on the stable PPA.

Development packages are available on the nightly PPA, if someone wants to take the risk.

The Mint folks have made an effort to remove Cinnamon's reliance on pieces of Gnome and explicitly give first priority to making it work well on Mint.

---

### Post by w00sterf1 on 2014-05-08
I'm running Cinnamon nightly. 

It works just fine except for one irritating issue, from time to time, the screen freezes and I can not access anything. I then have to switch to a text console and do a 'ps -ef | grep cinna' to find the 'cinnamon --replace' PID, kill it and then switch back to the graphical console as it will have been restarted by now and we are back at normal.

Other than this, I have had no issues with the nightly build.

---

### Post by ttuura on 2014-05-17
I'd like to point out this: [http://forums.linuxmint.com/viewtopic.php?f=61&t=167289](http://forums.linuxmint.com/viewtopic.php?f=61&t=167289) where glebihan basically says he is retiring the cinnamon-stable ppa for good.

[Select quotes:]("http://forums.linuxmint.com/viewtopic.php?f=61&t=167289#p859878")
> [I][COLOR=#333333][FONT=Lucida Grande]As for the reasons, there are of course several ones, the main one probably being that many people were wrongly seeing that PPA as providing official Ubuntu packages, when it never was official and actually contained Mint builds.
[/FONT][/COLOR][/I][--]
> [I][COLOR=#000000][FONT=Lucida Grande]In all honesty, I also hope that someone will finally step up on Ubuntu's side to provide decent Cinnamon packages, thus effectively making the PPA useless.
[/FONT][/COLOR][/I]
however, there seems also to be this, for trusty users at least:

[https://launchpad.net/~kranich/+archive/cubuntu](https://launchpad.net/~kranich/+archive/cubuntu)

---

### Post by Bashing-om on 2014-05-17
ttuura; Good input !

My Welcome to the forum;

Where good things happen.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]1 for all and all for one
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

