---
title: "Problem upgrading kdelibs-data"
date: 2005-05-02
forum: Desktop Environments
---

### Post by electricinkpen on 2005-05-02
I am having trouble using Synaptic's "Smart Upgrade" feature.

The only package I have that needs upgrading is kdelibs-data, from 4:3.4.0-0ubuntu3 to 4:3.4.0-0ubuntu3.1

When trying to upgrade, I get the following error:

E: /var/cache/apt/archives/kdelibs-data_4-0x1.687820000005ap-1363.4.0-0ubuntu3.1_all.deb:  trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf

...and I can't remove knetworkconf without removing the whole KDE package.

What should / can I do in this situation?

Thanks!

-eip

---

### Post by David R on 2005-05-02
I have the same problem, but I was able to remove knetworkconf without removing the whole KDE package.

But it seems that I should'nt had done this :

After rebooting, KDE mets several errors, and didn't launched correctly (the "K button" on the left bottom corner was missing, as well as the applications icons, and  the 4 desktops buttons on kicker).

It was a fresh install, so I decided to re-install kubuntu.

So now I think I will wait a bit before trying to reinstall this new version of kdelibs-data.

---

### Post by GeneralZod on 2005-05-02
There have been several threads about this (I've experienced it myself!) so the good news is that you are not alone :) Since it is so prevalent, I'd guess that the devs are working on updated packages, but obviously don't know for sure.

It would be nice to have some kind of working service pack for Kubuntu that fixed up some of the most obvious flaws.

---

### Post by epb613 on 2005-05-02
Not to say I don´t appreciate the hard work that the dev´s  have volunteered for us, but at the same time, this problem has been around for 2 weeks already, it´s affecting tons of people, and it shouldn´t be too hard to fix (or at least remove from the repository), and they haven´t given us any notice that they´re even aware of the problem. If this kind of thing is going to happen frequently in kubuntu, then alot of people are going to be very quickly switching distributions which would be a real shame.

---

### Post by jakel2k on 2005-05-02
[http://ubuntuforums.org/showthread.php?t=25294](http://ubuntuforums.org/showthread.php?t=25294) 

Another thread on the same topic.

---

### Post by coldsalmon on 2005-05-03
I agree, if something like this happens again and it is not fixed for this long without even a response from development, I will most likely switch to Debian.  Is there something I am missing?  It seems like Ubuntu is too good of a distro to let something obvious like this happen.  The worst thing is that I really like this distro, and think it has many great things going for it, but how am I supposed to brag to my friends about apt-get if it just breaks my desktop?

Seriously upset,

--C

---

