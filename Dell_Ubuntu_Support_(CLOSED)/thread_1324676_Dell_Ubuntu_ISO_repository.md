---
title: "Dell Ubuntu ISO repository?"
date: 2009-11-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Trevoke on 2009-11-12
[http://linux.dell.com/files/ubuntu/](http://linux.dell.com/files/ubuntu/)

Is anyone familiar with this? Are the images on there compiled for the Atom processor? Do they have support for the poulsbo, or whatever that annoying required video driver is?
Do they work for the Dell Mini 10v?

I couldn't find these answers, so I come to you for help.. :)

---

### Post by mikewhatever on 2009-11-12
You can read about the isos and what additional packages are included [-->HERE<--.]("http://en.community.dell.com/wikis/linux/building-base-ubuntu-factory-iso.aspx") As far as I know, Hardy 8.04 is the only version of that has poulsbo driver by default. I also rather doubt the isos are optimized for Atom cpu, since Dell preinstalls Ubuntu on non-Atoms too. I don't quite see why use those isos, they are almost the same as Ubuntu proper, flash and ATI/Nvidia apart. If you want lpia architecture, get it from [-->HERE<--.]("http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-alternate-lpia.iso") The only problem with that iso is, it's not a live one, and the installer isn't as pretty or easy to use.

PS Mandriva one isos should support poulsbo by default.

---

### Post by Trevoke on 2009-11-12
Okay; are there currently poulsbo drivers that are compiled for whatever version of the kernel comes with the lpia karmic koala that you linked? Because it would be really nice to go up to 9.10, but I really really want the graphical interface to work properly.

Right now I have a manually-upgraded 9.04 from the Dell version of it, and whatever Google gave me to install the poulsbo drivers on it, but my netbook "freezes" a little too regularly (everything stops responding, though the mouse keeps moving), and I can't think of any kind of CPU activity that would justify that.. But that's for another thread.

---

### Post by mikewhatever on 2009-11-12
As you might know, the current Ubuntu - poulsbo relationship is really messy. Jaunty has packages for poulsbo from its mobile repository that work quite well with some hacking. Apparently, there are both i386 and lpia versions, but I can't vouch for lpia. 
[Instructions for Jaunty]("http://ubuntuforums.org/showthread.php?t=1229345&highlight=gma500")

Karmic is a different story, cause the same packages for Jaunty don't work. Some reported poulsbo to work on Karmic with different packages, but I don't think there was an lpia version.

[http://ubuntuforums.org/showthread.php?t=1274343&highlight=gma500&page=2](http://ubuntuforums.org/showthread.php?t=1274343&highlight=gma500&page=2)

---

### Post by Trevoke on 2009-11-16
Thanks Mike!
This thread got me all set up on Karmic :
[http://swiss.ubuntuforums.org/showthread.php?t=1253406](http://swiss.ubuntuforums.org/showthread.php?t=1253406)
There was one small snag with the wireless driver not being recognized, and sadly I didn't store the page that solved that, but it was also on this forum, and it was a really quick and simple google search.
My Mini 10v now is happily running 9.10.

---

### Post by snowpine on 2009-11-16
Hi Trevoke, the Dell Mini 10v uses Intel 945 graphics (you can test this yourself with the terminal command 'lspci'). You do not need Poulsbo drivers, as you do not have GMA500 graphics. "Regular" Ubuntu should run just fine on your 10v. It is the Dell Mini 10 (no v) and Mini 12 models that require special drivers.

ps You should be able to get the wireless working by going to System->Administration->Hardware Drivers and choosing the Broadcom STA driver. You'll need to be connected through a wired connection.

I have a Dell Mini 9, which is almost the same as your 10v, so let me know if you have any follow-up questions.

---

