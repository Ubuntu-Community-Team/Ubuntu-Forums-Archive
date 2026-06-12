---
title: "fifteen minute hang on startup"
date: 2009-02-18
forum: General Help
---

### Post by Purposeful1 on 2009-02-18
Hi,

I'm running ubuntu-eee 8.04 (or 8.10, i'm not 100% sure) on my EEE PC 900, and it had been working pretty well for the past couple of months.  However, in the past week or so, I seem to have run into a few problems.  At first, sometimes when I started the computer, I'd just get a blank screen.  No biggie, I'd restart and it would usually work fine.I didn't do really much of any tweaking, but I left the default xandros on a partition.

Recently, though, when I start the computer I am able to log on to ubuntu, but when the desktop loads it hangs.  If I hover my mouse over an icon, it is detected (for example, hovering over the firefox icon makes the "Firefox Browser" bubble pop up), but clicking on that makes the cursor go to the busy signal momentarily, and then nothing else happens.  Firefox doesn't load.  Alt+F1/F2 similarly do not work.  I noticed as well that the battery icon and keyboard icon do not load until the computer "unhangs" (usually after about fifteen minutes of sitting there), and then all the applications i TRIED to open suddenly open.

Also, sometimes the upper toolbar thing (home, clock, battery icons/shortcut bar) doesn't load at all.  I usually end up restarting until the limited bar shows up, then wait for fifteen minutes until it unhangs and the computer becomes usable.

I am running compiz fusion (as I have since the beginning of using ubuntu), i regularly install updates, and I don't install very many programs or do much in the way of tweaking (I'm relatively new to linux).

Any suggestions?

Thanks

---

### Post by linux_tech on 2009-02-18
A few suggestions- To see if hanging is due to excessive memory or cpu utilization- monitor the processes that are running using htop.  scale down > system>preferences>sessions, run only that which is needed, see if performance improves.  Check performance while using your applications to find bottleneck. Also run a memtest to make sure memory is ok. Check for any messages, errors, etc (dmesg)

---

### Post by Purposeful1 on 2009-02-19
memtest seemed to run fine, but when I tried to install htop, I got this error message:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


the package manager has been acting up recently: right now it wants to remove some 360 packages (which seems like a lot to me), including things like openoffice.org, which i don't believe was upgraded.

If I try to remove the packages as suggested, it comes up with the error:


dpkg: parse error, in file /var/lib/dpkg/available' near line 1925 package xulrunner-1.9':
  junk after word in 'priority' field
E: Sub-process /user/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

---

