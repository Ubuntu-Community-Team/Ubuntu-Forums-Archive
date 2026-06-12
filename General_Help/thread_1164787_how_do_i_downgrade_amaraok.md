---
title: "how do i downgrade amaraok?"
date: 2009-05-20
forum: General Help
---

### Post by c/Kr3t on 2009-05-20
i was really impressed with amarok in the past. it was easy to setup devices, it was easy to organize my collection, it was better to navigate.

to my dismay, when i installed ubuntu 9.04, i was eager(?) to try out 2.0. it was alright, i liked the gui setup and everything was in sight and in mind so my music time was fast to play but recently it's been messing up royally.
At first it wouldn't play mp3's at all. so i spent a whole day converting 5000 songs to .ogg just to listen to them on my computer. but then when it came to putting them on my ipod, amarok dropped the ball once again and wouldn't copy them over. so, long story short, i have to rely on the retarded offsping of bill gates just to get the apple miracle, made by the toddler steve jobs, to hold my damn songs! >:(

so, i want to downgrade from this crap amarok to the old one that actually worked.

can anyone help me?

---

### Post by KhurramM on 2009-05-20
This might be risky, but its still worth trying:

Just download the old *.deb of Amarok and other deps for it.

Try installing amarok and its core deps, using dpkg.

This will downgrade amarok. But how much u need to downgrade, I cant tell that. U just have to do it via cli.

Hope this helps u.

**_A piece of advice:_** Whenever u wanna try something new, give it time to install and prove it self, then upgrade to the newer version permanently. There may be un-known bugs in the new upgrade.

---

### Post by mb_webguy on 2009-05-20
You can add [this repository]("https://launchpad.net/~bogdanb/+archive/ppa") to your software sources, then install the [amarok14]("apt://amarok14") package.  This will replace Amarok 2 on your system and prevent your system from constantly trying to update to Amarok 2.

---

### Post by c/Kr3t on 2009-05-20
> **mb_webguy said:**
> You can add [this repository]("https://launchpad.net/~bogdanb/+archive/ppa") to your software sources, then install the [amarok14]("apt://amarok14") package.  This will replace Amarok 2 on your system and prevent your system from constantly trying to update to Amarok 2.

thanks

---

