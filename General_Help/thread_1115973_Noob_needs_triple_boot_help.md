---
title: "Noob needs triple boot help"
date: 2009-04-04
forum: General Help
---

### Post by mustangman198129650 on 2009-04-04
I have decided to attempt to triple boot kalyway's mac OS, XP, and Ubuntu.  I am starting from a clean slate, and just need to know what order to install each OS. Also how to partition these, 9i know i need a partition for each os and a swap partition) as well as make one of the three bootloaders function.  I'm fairly comfortable with xp, but I'm still a Linux noob (I look up tutorials and copy/paste command line code to solve my linux issues on my main PC lol) Also I'll be installing the kalyway mac OS for the first time.  Needless to say I'm lost in this pursuit, and haven't been able to find a tutorial that allows for my lack of knowledge and general non-Uber-ness.  PLEASE help me get this done, i would love to be able to have such a flexible set of OS options.

I am crossing my fingers for some of the storied benevolence of the ubuntu community :)

---

### Post by 3Miro on 2009-04-04
I would make four partitions for the three systems plus swap (make it little bigger than your ram). You can partition things from the Ubuntu LiveCD using gparted (System -> Admin -> Gparted).

For the order of install, well I am not sure. I would assume that Ubuntu has to come last, since by default it will recognize the other OS (Ubuntu plays nice with other OS, other OS are mean or simply dumb). I would assume XP is the "meanest" i.e. it will not recognize other OS and would make it hard for you to boot them.

To dual-boot XP/Linux -> install XP and then Linux. I don't know what OSX would work. I would try: XP then OSX then Linux, it should work fairly easily (i.e. without the need to manually edit GRUB), but I cannot be sure.

---

### Post by mustangman198129650 on 2009-04-05
well I'm currently re-wiping my hard drive on the pc that i targetted for this triple boot experiment.  I spent this whole saturday bouncing from one breadcrumb of help to another, and I finally got it to work.  I'm wiping the drive because I'm going to do it again and make a walkthrough so that noone has to go on the same 'vision quest" as i did (please forgive the 80's movie reference)  I have to say that 80% of the knowledge i found on this was on this forum, and for that i thank anyone who reads this and has ever answered a question for one of us hapless noobs lol.  Thanks again to everyone, your tips were helpful even if i had to go search every thread in existence to find them, bottom line I got my answer :)

---

### Post by easybake on 2009-04-05
> **mustangman198129650 said:**
> well I'm currently re-wiping my hard drive on the pc that i targetted for this triple boot experiment.  I spent this whole saturday bouncing from one breadcrumb of help to another, and I finally got it to work.  I'm wiping the drive because I'm going to do it again and make a walkthrough so that noone has to go on the same 'vision quest" as i did (please forgive the 80's movie reference)  I have to say that 80% of the knowledge i found on this was on this forum, and for that i thank anyone who reads this and has ever answered a question for one of us hapless noobs lol.  Thanks again to everyone, your tips were helpful even if i had to go search every thread in existence to find them, bottom line I got my answer :)

I would much appreciate a guide to do this. I tried doing this awhile back and kept getting the dreaded "HFS partition error". If you write a how-to i would appreciate a link to it.

A how-to in the tutorial section may not be approved simply because you are not technically supposed to install Osx on anything other than Mac hardware. 

If it doesn't get approved I would greatly appreciate a PM of it.

---

### Post by polkadotteapot on 2009-04-05
Hello,

I'm looking to do a triple boot xp/ubuntu/osx on my aao and found these useful [http://tgrounds.blogspot.com/2008/03/osx-leopard-1051-on-pc.html](http://tgrounds.blogspot.com/2008/03/osx-leopard-1051-on-pc.html) and go to [www.insanelymac.com](www.insanelymac.com) - these are the pioneers.

Let us know how your install went.

---

