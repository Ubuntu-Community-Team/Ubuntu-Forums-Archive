---
title: "Beryl on an Amilo laptop with Feisty"
date: 2007-05-08
forum: Desktop Effects &amp; Customization
---

### Post by NotoriousTF on 2007-05-08
Hey guys!
I've just installed Beryl on my Fujitsu Siemens Amilo L7300. I'm running Feisty. I'm not 100% sure, but I think its got a UniChrome PN800 integrated graphics card. I can't get Beryl to work at all, its installed & I've played around with the Settings Manager but to no avail. I've been trying to install good looking desklets and had a look at some dock's too. I've installed Avant Window Navigator it runs, but with a plain black boarder behind it, and running nearly a quarter of the way up the screen. It was suggested I install Beryl to fix that, and so far it hasn't helped.

So I'm wondering if anyone has had any success with Beryl and the laptop/graphics card I've named above. Trying to sort this out is really doing my head in!!

---

### Post by scarystuff on 2007-05-14
I would like to know how you managed to install Feisty on that laptop to begin with. I have the same model and it freezes somewhere when it starts to load the GUI. Do you have a guide or something?

I got Dapper to work, except I never managed to install the right gfx driver, so it was very slow.

---

### Post by NotoriousTF on 2007-05-16
Hey scarystuff, I had a similar problem using the live CD. I couldn't install Feisty or boot it from the CD. I read somewhere that from Edgy you could use the update manager to upgrade to Feisty, so I moved up from Dapper to Edgy then used the update manager to upgrade to Feisty which worked a treat!

I did have problems with my resolution originally, it would only display in 800x600. So I used some of the advice given in this thread [http://ubuntuforums.org/showthread.php?t=411489](http://ubuntuforums.org/showthread.php?t=411489) which helped a lot. If I remember right I used the command:

sudo dpkg-rreconfigure xserver-xorg

This sorted out all my resolution problems, and it detected my graphics card too!
Hope this helps.

---

### Post by purpledavec on 2007-05-20
Hi, I have the Amilo Pro 2055 with a VIA Unichrome P4m800/CE video chip and I have researched like mad on the net and it appears that because there is no driver maintainer for VIA certain features beryl and suchlike require haven't been written in the driver - and are unlikely to be :-(

---

### Post by Ub1476 on 2007-05-20
See if there's a driver for your card in: System>Administration>Restricted Drivers Manager. If it is, you should use that driver. For the rest, I don't know your graphic card so ca't help you  much more:(

---

### Post by NotoriousTF on 2007-05-25
[quote=Ub1476]See if there's a driver for your card in: System>Administration>Restricted Drivers Manager.[/quote]

Gave that a try but the only response I got was an pop-up window with:

> Your hardware does not need any restricted drivers.

Does that mean there is probably none available?

---

