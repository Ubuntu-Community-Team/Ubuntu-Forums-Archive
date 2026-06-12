---
title: "Overall laptop trouble - Dell Inspiron 6000"
date: 2007-10-10
forum: Dell  Ubuntu Support
---

### Post by Acoustyk on 2007-10-10
I'm new to Ubuntu(and linux in general) and I just upgraded from Feisty to Gutsy and am regretting it.  Apparently there is some driver discrepancy with ATI x--- series cards and mine is one of those.  The driver I have now is terribly slow (even slower after I installed an xgl package that I thought would help).  I have looked around for a problem and I noticed that my xorg.conf file is... well three files xorg.conf.1 , xorg.conf.2 , and xorg.conf.3 

I can't rename one of the three files to the standard xorg.conf because I dont have root abilities and can't login as root.  (is there a different password by default other than what you choose?)

Also my battery life is **** now.  I don't want to blame Ubuntu for this until I fix this problem and can test it properly but has anyone heard of this side-effect on dual boot laptops?

If no one has a clue about this could someone direct me to a site where I can get directions on how to due a clean reinstall over top of my existing partition?  Ubuntu was a dream come true until all this mess and it's kind of disappointing. :(

---

### Post by notwen on 2007-10-10
> f no one has a clue about this could someone direct me to a site where I can get directions on how to due a clean reinstall over top of my existing partition? Ubuntu was a dream come true until all this mess and it's kind of disappointing.

If you have a Feisty LiveCD, just pop it in, and select format the entire partition during the install.  As far as your issues go, Have you checked out the [Gutsy Dev forum]("http://ubuntuforums.org/forumdisplay.php?f=238")?  Lots of issues are generally made known there by the users, maybe someone else has had similar issues and a work-around/fix may already be available.  Good luck.  =]

---

### Post by usmanlinux on 2007-10-11
> **Acoustyk said:**
> 
I can't rename one of the three files to the standard xorg.conf because I dont have root abilities and can't login as root.  (is there a different password by default other than what you choose?)

go the terminal and run 

sudo -i

this will log you on as admin, and the pass is the same as your user account. if you are the account that installed it.

> Also my battery life is **** now.  I don't want to blame Ubuntu for this until I fix this problem and can test it properly but has anyone heard of this side-effect on dual boot laptops?(

this is not from dual boot, my 6000 battery bit it also.. it just something that happens.. sorry.. my battery died on my after having the laptop for 4 months.. i had to buy a new one..

---

### Post by thisbeadam on 2007-10-31
That sucks about your battery, and here is why. I just upgraded (last week) to linux 7.10 and the first thing i get is a little warning box saying that my battery is bad. then another box saying I could have a faulty battery from dell. WELL, I did, which I knew my battery was messed up, but I haven't cared to get a new one (aka had the money) anyways, the warning box gave me a link to dell and well long story short, I got a brand new battery shipped and all for FREE. I just got it today, man, I missed having freedom.:mad:

---

