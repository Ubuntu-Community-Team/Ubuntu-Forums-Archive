---
title: "upgrading from kde 4.5 to 4.6"
date: 2011-09-03
forum: Desktop Environments
---

### Post by bananagins on 2011-09-03
ok as the title says, i'm trying to upgrade from kde 4.5 to kde 4.6. i have ubuntu 10.10 maverick installed (running both GNOME and KDE). i looked around and apparently, i need to add ppa-kubuntu/backports repository to upgrade to 4.6 but according to here:
[http://www.ubuntuupdates.org/ppa/kubuntu-ppa_backports?dist=maverick](http://www.ubuntuupdates.org/ppa/kubuntu-ppa_backports?dist=maverick)
all packages were deleted from maverick! why?? i looked all over the web but can't find an answer. 

so, someone, please if you know why they were deleted, or more importantly, how i can upgrade to kde 4.6, please help me. i'm so confused.

p.s., i do not want to upgrade to 11.04 or 11.10. it took me forever to get everything working just right in 10.10 and i'm happy using this for a while. so yes, i know that upgrading to natty would allow me to upgrade to kde 4.6 but i'd like to get it working on 10.10! any help appreciated!

---

### Post by SeijiSensei on 2011-09-03
You're out of luck.  There are no Maverick packages in the backports PPA.  There were packages for 4.6.x, but they were deleted when KDE 4.7 was released.  So now you have the choice of 10.10 with 4.5.5 or 11.04 with KDE 4.7 via backports.

I had 10.10 plus the 4.6 packages installed, then had to reinstall.  When I went to get the 4.6 packages again they were gone.  I had hoped they might have been hiding in /var/cache/apt on a similar machine, but they weren't there.

I'm planning on testing out 11.10 again; I had bad luck with an early alpha release, but it's now in [beta]("http://www.kubuntu.org/news/kubuntu-1110-beta-1-released").

You might want to browse [this thread](http://ubuntuforums.org/showthread.php?t=1813368).

---

