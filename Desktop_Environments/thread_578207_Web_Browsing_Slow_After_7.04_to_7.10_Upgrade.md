---
title: "Web Browsing Slow After 7.04 to 7.10 Upgrade"
date: 2007-10-17
forum: Desktop Environments
---

### Post by Tahi_Kiwi on 2007-10-17
I viewed the matching topics about this, but none applied. I could not locate a Gutsy (7.10) specific forum, so here I am.

Situation: Yesterday successfully ran the upgrade from 7.04 to 7.10RC.
Problem: Compared to 7.04, Web browsing in 7.10RC is __much__ slower. That is, painfully slower.
For Comparison: I still have a separate installation of 7.04-based Ubuntu Studio, and everything still runs fine there. That seems to eliminate my router, DNS settings, my host OS (I'll get to that), or my otherwise swift DSL connection.

Environment: Am running Ubuntu distros (Studio and 7.10RC) as guests OS's through VMWare Player, which runs under the same Windows Vista host (although not concurrently--I never load more than one virtualized session at a time).

Mind you, please, that previously installed 7.04 and still-installed Ubuntu Studio ran/run fine. So what is different between 7.10RC and 7.04's ability to run as virtualized PCs, specifically as it pertains to Web access?

Any ideas? I think that I have eliminated "outside" factors because Ubuntu Studio still runs great.

By the way, the browser is Firefox 2.0.0.6.

Thank you

---

### Post by Tahi_Kiwi on 2007-10-17
Could there be some file cleanup that I need to perform after the upgrade to 7.10RC? 

If so, how do I run that, please.

Thank you.

---

### Post by cubejockey on 2007-10-17
is there something purposely restricting speed until the official release?

---

### Post by Tahi_Kiwi on 2007-10-17
I do not know. Given the open nature of Ubuntu, that would surprise me.

---

### Post by SticMAN on 2007-10-19
This is not only with the upgrade! I've found this on a fresh installation also!

So BAD and disappointing!

I've done Both i386 and amd64 installs, and the webbrowsing is so slow!
I've scanning for possible solutions, but none yet!?

I forgot to mention, i'm running on a Dell dimension 9200, which is supposed to be one of the BIGGEST supporters of this OS and still i had to do numerous patches,Hacks Tricks to get even the basic sound and display to work!

I'm going back to 7.04 and it will take a LOT of convincing to get me to upgrade!

Blackie
ps C'mon Mark, fix it or just DO something already!!

---

### Post by zyg0t3 on 2007-10-19
I seem to have run across this problem as well. It almost seems like a DNS problem as it takes a moment for the browser to locate the site. I haven't done any indepth research into it as i thought it was only me and could have been problems with my generic wifi router. 

But, seeing as how others are having this problem as well.

Do we know if it is occurring on systems other than laptops. As that's what i'm using and I can vouch that it is happen on fresh installs, as i installed from a RC1 disc

---

### Post by Asraniel on 2007-10-19
i'm very sure this is the ipv6 problem (THAT SHOULD BE FIXED!!!). Search the wiki for ipv6 and you will find the solution

edit: and please make a bugreport, it's not normal that this bug that was fixed some time ago is back again. the fix is out there, i have no idea why the devs left it out.

---

### Post by zyg0t3 on 2007-10-19
Nice, Thanks for the headsup Asraniel. The firefox fix worked, haven't done the system wide change yet. But this validates your assertation. 

If anyone is looking the link is here:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

just search for ipv6

> **Asraniel said:**
> i'm very sure this is the ipv6 problem (THAT SHOULD BE FIXED!!!). Search the wiki for ipv6 and you will find the solution

edit: and please make a bugreport, it's not normal that this bug that was fixed some time ago is back again. the fix is out there, i have no idea why the devs left it out.

---

### Post by runningrascals on 2007-10-20
I found [this post]("http://techxplorer.com/2007/02/22/slow-browsing-using-firefox-on-ubuntu/") to fix my problem:

---

### Post by zyg0t3 on 2007-10-20
Yup, its the same fix.

---

### Post by Tahi_Kiwi on 2007-10-20
Ah, thank you all so much for this solution.

The disabling of iPv6 in the FIrefox config fixed the problem.

I didn't have this problem running Firefox under Ubuntu 606, 610, or 704. It cropped up only after upgrading to 710.

---

### Post by Marko_J on 2007-10-24
I had this exact problem after upgrading to 7.10. Fixed now, thanks a lot :)

---

### Post by sKaD on 2007-11-05
I know this is an old thread, but just wanted to post and state that this fixed my problem and I just barely installed this a few days ago, so I'm sure others are probably experiencing this issue.

---

