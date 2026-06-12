---
title: "run AOE2 using Wine?"
date: 2007-01-06
forum: Gaming &amp; Leisure
---

### Post by mkent91 on 2007-01-06
How do i run age of empires two: the age of kings using wine? I have the cd and i cant figure it out! im confused on using wine](*,) i dont even know where to go to run wine:(

---

### Post by patrick295767 on 2007-01-06
This one, I run it great with cvscedega (free)

---

### Post by jodrre on 2007-01-06
I'm pretty sure that Wine doesn't support gaming.  I've got pretty good reports (haven't tried myself, I don't game a lot) about Cedega ([www.transgaming.com)](www.transgaming.com)).  It started from Wine, so we know it's good, but it does cost money (about $15 for 3 months).  It comes with a free 2-week trial.  Download the demo by going to transgaming.com/linux_products.php.  Pay attention to the driver details, becuase it'll be hell if you try to play your games with a subscription and it doesn't work.  Get to terminal and type

sh /PATH_TO_INSTALLER/cedega_timedemo_installer


Be sure to replace the text in bold with where the demo is saved (save to your desktop, it'll make things easy)  This will only install it for your username, so put sudo in front if you want to let everybody on your system use it.  Agree to everything, then check your email.  It'll do some tests.  When it finishes with that, go back to Terminal and type

~/cedega_timedemo

That will pull up the GUI.  Click install, put the CD in the drive, then browse to the installer on the CD and run through that installer.

Hope this helps!

Joe R

---

### Post by jodrre on 2007-01-06
> **mkent91 said:**
>  i dont even know where to go to run wine:(

You can run wine by going to Terminal and typing

winecfg

It looks like Windows 98.  You can choose what version it will emulate (from 95 all the way to XP)

---

### Post by mkent91 on 2007-01-06
how do i get cvscedega???

---

### Post by cezdeville on 2007-01-06
> I'm pretty sure that Wine doesn't support gaming

not true. i'm using Wine for playing:
Diablo II -LOD
Warcraft III demo
Regnum Online windows version (with 3D acceleration)

in the past i've also tried:
Fallout1
Fallout2
Fallout Tactics
Baldur's Gate
Icewind Dale II
Starcraft
and more...

they all worked just fine with Wine, and it's much simplier to install Wine that cvsCedega.

> How do i run age of empires two: the age of kings using wine?
i'm not sure how this one work with wine, haven't tried it yet. the simpliest way would be to put your cd in drive and r-click setup.exe (or whatever it is called).  thet you choose: open with... and pick-up Wine from list (of course only if you have this one installed).
main disadvantage of this method is that if something goes wrong, you will not see what's the matter.
for more advanced usage type in terminal: wine /path/to/your/program/file.exe
this time you will be able to check all terminall messages and errors (in case they occure).

good luck!

---

### Post by patrick295767 on 2007-01-06
[www.linux-gamers.net/](www.linux-gamers.net/)
is first place to go

---

### Post by Enverex on 2007-01-10
Age of Empires 2 works ok with Wine, the menu is rather slow due to current DDraw issues that are being ironed out but you can speed that up by changing your DD renderer to opengl ([http://wiki.winehq.org/UsefulRegistryKeys)](http://wiki.winehq.org/UsefulRegistryKeys)). Ingame seems to run perfectly. CVSCedega is rather old and broken so kudos for getting it to play anything but I'd not use it for the long-haul.

Jodrre: Have a look at [http://appdb.winehq.org](http://appdb.winehq.org) . Wine supports a lot of games.

---

