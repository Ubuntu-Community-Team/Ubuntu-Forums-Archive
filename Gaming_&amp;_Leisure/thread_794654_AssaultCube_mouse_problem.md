---
title: "AssaultCube mouse problem"
date: 2008-05-14
forum: Gaming &amp; Leisure
---

### Post by kundalinikat on 2008-05-14
Hey, I am using Hardy for AMD64, my installation is pretty new.

I would love to tell you my graphics card or its driver or my mouse configuration, but I am having trouble finding any information about my graphics card. Seriously what happened to the 'system information' part in the System->Administration menu? And I cannot remember the command that lists active drivers from which I might pick out the graphics card information...

I installed AssaultCube from source (after getting needed libraries, at first it didn't tell me I'd need G++ and automake/autoconf, so i felt kinda stupid) and there were the usual screenfulls of errors but it never quit out of the installation except when I was missing those libraries. At which point I 'make clean'ed and installed the libs. Nothing out of the ordinary :)

The game starts and everything seems to work well (at least I tried bot matches) except that the mouse does not respond! I am stuck facing in one direction.

There is a thread about this same problem on the AssaultCube forums, but it devolves into stupidity pretty quickly (and anyway those forums are not Linux-specific).

Any help please? thanx in advance, I think i will really enjoy this game once i can fix this.

---

### Post by amirhomayoun on 2008-05-28
I am having the same problem. Although I am playing the cube for 2-3 weeks (on hardy) and this problem happens haphazardly. Most of the time there is no problem at all. But today this mouse problem is combined with my game changing from full screen to windowed mode. To resolve that I disabled the Decoration plugin from Compiz. Now I have the full screen game but the mouse problem exists.

------------
Update: My problem solved. I just extracted the file AssaultCube_v0.93.tar.bz2 into a directory and restarted a fresh copy. everything is fine for now.

---

### Post by carlinuxlearner on 2008-11-26
Dido kundalinikat, I've got the same problem.

Any body going to help us out?

---

### Post by 73hunter on 2008-11-26
I agree with you!![img]http://links.longhainet.com/haha.jpg[/img]-----------------------------------------------------------------------------------------------------------------------------------Signed Network: Not A Bad Man, A Woman Does Not Love!Recommendation:[Game Machine](http://www.macrown.com/game_machine.asp) / [Gaming Machine](http://www.macrown.com/gaming_machine.asp) / [Slot Cabinet](http://www.macrown.com/slot_cabinet.asp) / [Gambling Cabinet](http://www.macrown.com/gambling_cabinet.asp) / [Pile Up Machine](http://www.macrown.com/pile_up_machine.asp)

---

### Post by gigaferz on 2008-11-26
why dont you save yourself from that (been there) 

Remember this getdeb.net !!!

---

### Post by noerrorsfound on 2008-11-28
> **gigaferz said:**
> why dont you save yourself from that (been there) 

Remember this getdeb.net !!!
How is a deb file going to solve his mouse problem? If you're referring to the original post, it's old anyway, since AC 1.0 comes with 64-bit binaries due to my begging.

Getdeb's deb files caused a lot of problems for people with version .93, and the best option was always to use the provided archive package.

---

### Post by chuckyp on 2008-11-28
Try disably desktop effects.  Hit alt+F2 and type in metacity --replace . To get the effects back you can use compiz --replace .  Just disable them and launch the game.

---

### Post by carlinuxlearner on 2008-11-28
Hey I got it working. I compiled it on my machine.

There is a How To here: [http://gwos.org/doku.php/guides:64bit:assultcube]("http://gwos.org/doku.php/guides:64bit:assultcube")

C@RL

---

