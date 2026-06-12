---
title: "HP nc8430 runs slow on AC, normal on battery"
date: 2008-08-11
forum: Desktop Environments
---

### Post by Darendo on 2008-08-11
Not long after Hardy was released I installed several updates for Gutsy (hadn't upgraded yet). The next time I restarted my notebook, I noticed it ran slowly. That quickly turned into unusably slow. And that turned into insanely unusably slow. I decided to give Hardy a try but experienced the same issue. The problem was inconsistent when running on AC power. Sometimes, like on the 10th reboot, it would run OK. However, and I just discovered this tonight, if I unplug AC power and run off the battery, the notebook runs normally. Plug AC back in and it immediately runs slower. Unplug, etc. _This is absolutely repeatable_. I actually have two of these notebooks and both exhibit the same behavior. The second notebook is brand new so this is definitely not a battery issue.

---

### Post by woaibbhemm on 2008-08-12
hello~
    nice   to  meet  you   and     thank  you   for   youe   sharing ,  welcome   to   our   website  !












Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by wakeman on 2008-10-12
Hi, I have exactly the same problem running Debian Etch on HP nx7300. I believe this problem is not related to distribution, it is hardware based. 
I noticed it first after during one of many laptop bootups, everything was suddently excruciatingly slow starting.
It might be that something got screwed up on the motherboard during one of the many switches from AC to battery and back.
One workaround that helped some people is:
 echo 1 > /sys/module/processor/parameters/max_cstate
I have no clue what to do but I'll still try with another power adapter.

---

### Post by gggard on 2008-11-28
I had the same problem on my HP laptop nc8430, the problem is present both on Windows XP and on Linux (even on the BIOS setup which is incredibly slow).

I have found the solution : my power adapter was guilty ! We I plug a new one everything work perfectly. The strangest is that with the faulty adapter the connection is detected by the OS and the battery is charging !

---

