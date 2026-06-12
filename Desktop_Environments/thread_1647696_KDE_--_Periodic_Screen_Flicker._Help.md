---
title: "KDE -- Periodic Screen Flicker. Help?"
date: 2010-12-17
forum: Desktop Environments
---

### Post by jimboUSAF on 2010-12-17
I recently installed kubuntu on my HP workstation xw4200. (vs. 10.10) Every six seconds or so, the screen flickers. I can't make out any windows or text -- but only portions of the screen go black, with some horizontal white bars.

I've run Kubuntu from the same live disk on an ASUS laptop, and didn't have this problem. When I ran the live disk on this computer, it flickered, but I attributed this to the disk running slower than a harddrive OS on an older system. In light of this, I'm figuring it's a graphics hard conflict; here's what this computer's running:
RV515 PRO [Radeon X1300/X1550 Series]

I'm loving Kubuntu, but the flicker is *very* annoying, and I'd love to find a way to fix it. After some googling, I found what I thought could be a solution -- but it was for an older version of Ubuntu, and the system settings directory had changed, and the Startup Service it referred me to was no longer there.

While I was in startup services, I tried disabling the 'Display Management display monitor', but this didn't solve the problem, though it flickered as I turned it on or off. I just hit 'stop' and waited until the next flicker... should I stop it then restart the system? (Or is that too XP of me... xD)

Anyone have any ideas?

---

### Post by inobe on 2010-12-17
if you know about ati drivers, they aren't very good, in fact in most cases the opensource driver is better.

you could try disabling desktop affects.

i believe if you are in a live environment, you are using the opensource driver.

here's a search for that video card [http://ubuntuforums.org/search.php?searchid=78151216](http://ubuntuforums.org/search.php?searchid=78151216)

a bunch of folks have problems with ati, it's not a linux issue, at best the drivers suck.

good news though, your system has a **PCI Express x16 Graphics slot** a great place to stick a cheap 6 series nvidia card ;)
[http://h18000.www1.hp.com/products/quickspecs/12022_div/12022_div.html](http://h18000.www1.hp.com/products/quickspecs/12022_div/12022_div.html)

now this will be almost trouble free, from inserting the card and enabling the nvidia driver in "additional drivers"

nvidia have much better linux drivers support, i never had issues with these cards.

---

### Post by mescobal on 2011-01-16
It could be related to this:

[http://forum.kde.org/viewtopic.php?f=111&t=92240](http://forum.kde.org/viewtopic.php?f=111&t=92240)

Marcelo.

---

