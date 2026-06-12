---
title: "graphical differences between ubuntu and fedora"
date: 2008-02-15
forum: Fedora/RedHat and derivatives
---

### Post by stlcoptony on 2008-02-15
Can anyone tell me why the blacklisted Intel X3100 965GM chipset works with compiz in fedora but not ubuntu?  Is this something that can be ported to ubuntu?

thanks

---

### Post by SunnyRabbiera on 2008-02-15
Usually a piece of hardware blacklisted on ubuntu is blacklisted for a reason, like if that driver causes severe issues with the system.
But I am sure there is a way to get it un blacklisted, just at your own personal risk.

---

### Post by stlcoptony on 2008-02-15
yeah, i know i can comment it out, but where is crashed on ubuntu (while playing videos, like the wiki and bug report said) it does fine on fedora 8. I have searched around and found a couple people who said that fedora was the only one that worked for them with the X3100.

I would, however, really like to use ubuntu. I was just getting used to it and now the new computer won't support all the features..

thanks

---

### Post by SunnyRabbiera on 2008-02-15
Well even though fedora and Ubuntu are based on the same system (linux) they both come from different philosophies.
If you want to use ubuntu instead but not have its issues you can give linux mint a shot, they have one heck of a team.
Mint usually patches things like this so even though it might be blacklisted initially it might be more stable under the environment.

---

### Post by stlcoptony on 2008-02-15
yeah, I tried them too, with no luck. I have thought about trying sabayon, but i have no knowledge of the gentoo base whatsoever. I tried researching the documentation on the website (gentoo's) and became lost quickly. Have you heard whether or not a better driver will be coming along for the X3100 chipset?

thanks

---

### Post by SunnyRabbiera on 2008-02-15
Not really, I know some distros have the chipset in question under ignore but this is done at your own risk.
Really ubuntu is not the only one with this issue, there are more distros out there with this chipset blacklisted for safety reasons.
But no one is forcing you to use fedora, you could use ubuntu without the desktop effect or get a better card.

---

### Post by igknighted on 2008-02-15
Fedora is almost certainly using a newer driver for that card.  Fedora 8 came out a month later than Ubuntu 7.10, Fedora tends to use newer/bleeding edge software more so than Ubuntu, and Fedora updates drivers and such mid release, unlike Ubuntu.  Taking into account these things, I would bet that the new driver just works better w/ CF and that is why you have the difference.

If you really want to use Ubuntu, try compiling the latest drivers yourself, or try out the newest alpha release of Hardy to see if anything has changed.

---

### Post by stlcoptony on 2008-02-15
Thanks everyone.

igknighted:  I have tried downloading the alphas of hardy, there were other bugs/strange things going on with the alpha release (but compiz did work...). Anyway, how do i go about compiling the latest driver for the Intel 965 GMA X3100 chipset? Where can i download the source code (assuming it's source code since I'll be compiling it)

thanks

---

### Post by igknighted on 2008-02-15
> **stlcoptony said:**
> Thanks everyone.

igknighted:  I have tried downloading the alphas of hardy, there were other bugs/strange things going on with the alpha release (but compiz did work...). Anyway, how do i go about compiling the latest driver for the Intel 965 GMA X3100 chipset? Where can i download the source code (assuming it's source code since I'll be compiling it)

thanks

I do not know where the driver could be found (at least the source)... if you want to really experiment, try using alien to simply install the Fedora package on Ubuntu.  More than likely it will fail, but if its a test partition who cares.  You could also look at the specfile for Fedora's and see what sources they are using and how they install it, then try to mimic that when you install

I'm sure there are guides for updating that driver somewhere... just search around.  The methods I suggested in the first paragraph should be last resorts only, I really don't know where to find the official source.  I would start at the x.org site and intel's site.

---

### Post by stlcoptony on 2008-02-15
Thanks

(I am beginning to wonder if it would be easier to install the Nvidia card in the notebook...)

---

### Post by SunnyRabbiera on 2008-02-15
> **stlcoptony said:**
> Thanks

(I am beginning to wonder if it would be easier to install the Nvidia card in the notebook...)

Possibly as at least nvidia is mostly co operative

---

### Post by stlcoptony on 2008-02-15
how hard would it be to acquire an Nvidia 8400gs and install it? Is it even possible with the intel chipset already being there?

---

### Post by igknighted on 2008-02-15
> **stlcoptony said:**
> Thanks

(I am beginning to wonder if it would be easier to install the Nvidia card in the notebook...)

Just wait for Hardy, it should be stable enough by the time it hits beta.  I would strongly recommend you stay with intel because the drivers are open source.  If you had this bug on an nvidia card, you might wait years for it to get fixed.  With intel, its the next release.

And changing the graphics card in a notebook is not really a realistic thing.  Notebook hardware for the most part is what it is.

---

### Post by stlcoptony on 2008-02-15
> **igknighted said:**
> Just wait for Hardy, it should be stable enough by the time it hits beta.  I would strongly recommend you stay with intel because the drivers are open source.  If you had this bug on an nvidia card, you might wait years for it to get fixed.  With intel, its the next release.

And changing the graphics card in a notebook is not really a realistic thing.  Notebook hardware for the most part is what it is.

I have seen a couple of the bug reports stating that the X3100 has been taken off the blacklist for Hardy, but that the performance was still horrible (I am assuming this is due to the driver because this actually seems like a very nice integrated graphics chip). I really hope this is fixed in the next release, as then I can get rid of vista and Media Direct...

---

### Post by WinLinSolCoder on 2008-02-16
> **igknighted said:**
> Fedora is almost certainly using a newer driver for that card.  Fedora 8 came out a month later than Ubuntu 7.10, Fedora tends to use newer/bleeding edge software more so than Ubuntu, and Fedora updates drivers and such mid release, unlike Ubuntu.  Taking into account these things, I would bet that the new driver just works better w/ CF and that is why you have the difference.

If you really want to use Ubuntu, try compiling the latest drivers yourself, or try out the newest alpha release of Hardy to see if anything has changed.

Fedora is also the base for Red Hat Enterprise Linux, and hardware vendors go out of their way to support Red Hat (and Novell SuSE after Red Hat, of course).  There were some ATI drivers that would install under Red Hat Enterprise Linux and Fedora Core no problem, but crash under Ubuntu.  My systems with ATI cards cannot even boot the Ubuntu Live CDs - instead, crashing on bootup due to driver issues with the cards.

Driver updates mid-release are rather important (every other major OS/distro provides them (RHEL, SuSE, Windows, even Solaris) :( ).  They should sort that out and get it rolling, IMO.

I had SuSE subscriptions for both my developer machines and my server (they're rather cheap :) ), but I've been trying to run Ubuntu since 6.06LTS was released and have been unsuccessful since then.

---

