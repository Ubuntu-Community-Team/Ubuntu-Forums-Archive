---
title: "Humble Bundle Stats &amp; Visualisations"
date: 2012-03-27
forum: Gaming &amp; Leisure
---

### Post by Cheeseness on 2012-03-27
Hi there fellow Linux gamers!

I recently finished writing [an article]("http://cheesetalks.twolofbees.com/humbleStats.php") that attempts to explore  and interpret what all those numbers and fancy charts might mean. In  addition to my own thoughts and opinions, the article is also sprinkled  with quotes and anecdotes from top Humble Bundle contributors including  Notch (Minecraft developer), Garry Newman (Garry's Mod developer),  TPJeff (of Team Phobic), ExpiredPopsicle (of Cryptic Studios),  NimbleDave (of NimbleBit), Mt.Gox (a Bitcoin site whose CEO is excited  about indie games) and tantepose (a technology journalist with  DinSide.no).

I talk a bit about Linux gaming and Linux gamers (as well as other platforms),  and I also touch on the open source projects that have come out of the  Humble Bundle promotions.


I've also created a self-updating page called the [Humble Visualisations]("http://cheesetalks.twolofbees.com/humble/") that aggregates and calculates statistics from all Humble Bundles past and present. So far as I'm aware, it's the only place on the internets where stats from all bundles can be seen and compared on a single page.

Enjoy!

---

### Post by oldrocker99 on 2012-03-28
It is always great to see that Linux users pay extra!

---

### Post by BcRich on 2012-03-29
Excellent work [Cheeseness]("http://ubuntuforums.org/member.php?u=1594166")! A fascinating set of data to work with and very thoroughly considered representations, thereof.
One thing I was hoping to see visualized re. HIB and "H non-indie B" is how the sales of the bundles are effected (if at all) after the bonus games have been announced. This can still be classed as data that is acquired from the HB website, right? The catalyst could have perhaps been the day that HB officially sends the email announcing the bonus games. I'm just curious as to why that data wasn't included :)

---

### Post by madjr on 2012-03-29
nice work!

---

### Post by Zeven on 2012-03-31
Very interesting read, thanks! I will be using this as evidence myself when I need to argue the case for Linux in the future.

---

### Post by Ludd1te on 2012-04-06
I agree--great article.  Thanks!

(And, yeah, it's neat to see GNU/Linuxers pay the most.  :  )

---

### Post by Cheeseness on 2012-04-16
Hmm, so it seems that I'm not getting notifications for replies!

Thanks to everybody for the comments :D


For anybody who's interested, I've [updated]("http://cheesetalks.twolofbees.com/humbleStats.php") the analysis article with some extra quotes from the Humble Brony Bundle guys. The update also adds a couple more charts and tables, covering "separate  price" values for games in the bundles, the impact of bundle frequency  on total revenue, and some extra thoughts on what the Linux averages  might mean (I don't believe that they're indicative of Linux users  paying more - dun dun dun!).

In addition, the [Humble Visualisations]("http://cheesetalks.twolofbees.com/humble/") have been updated to include some extra numbers in the frequency table to help look at the impact of frequency on revenue, and new charts that show the fluctuation in "separate price" value for initial titles and bonus titles across the bundles.


> **BcRich said:**
> One thing I was hoping to see visualized re. HIB and "H non-indie B" is how the sales of the bundles are effected (if at all) after the bonus games have been announced. This can still be classed as data that is acquired from the HB website, right? The catalyst could have perhaps been the day that HB officially sends the email announcing the bonus games. I'm just curious as to why that data wasn't included :)

At the moment, I'm not keeping historical data. The values I store are replaced with whatever the current values are at the time that the Humble Bundle site is parsed, and that only happens when people visit the page (so not at regular intervals, which I think would be essential for getting that sort of information in a reliable fashion). Setting up cron jobs to make the process automated, and storing the retrieved values as time-series data isn't beyond me, but I don't have any plans at the moment to make that happen (but that doesn't mean I won't get excited about it in the future :) ).

If you haven't seen it, the 2011 GDC presentation that Jeffrey and John did is pretty neat, and has a little bit of information on how purchases fluctuated over time for the first two bundles. [http://www.gdcvault.com/play/1014437/The-Humble-Indie](http://www.gdcvault.com/play/1014437/The-Humble-Indie)

---

### Post by BcRich on 2012-06-03
Sorry, to resurrect an old thread but I just had to say (again) Cheeseness, I absolutely luv these visualizations :D 10 stars for sharing!!!!!

---

### Post by Cheeseness on 2012-06-03
> **BcRich said:**
> Sorry, to resurrect an old thread but I just had to say (again) Cheeseness, I absolutely luv these visualizations :D 10 stars for sharing!!!!!

Ha, I'm glad you like them!

I made a guest post on gamingonlinux.com earlier today which is a [summary of the recent Humble Bundle developers' Reddit IAmA](http://www.gamingonlinux.com/index.php?threads/the-humble-indie-bundle-v-reddit-iama-a-summary.887). It's not particularly stats related, but it does include a bit where I contacted Notch to ask which platform he selects for his contributions to be marked against. Apparently he chooses Windows, which means that our high Linux averages aren't supported by his often generous contributions :D

---

### Post by BcRich on 2012-06-03
> **Cheeseness said:**
> Ha, I'm glad you like them!

I made a guest post on gamingonlinux.com earlier today which is a [summary of the recent Humble Bundle developers' Reddit IAmA]("http://www.gamingonlinux.com/index.php?threads/the-humble-indie-bundle-v-reddit-iama-a-summary.887"). It's not particularly stats related, but it does include a bit where I contacted Notch to ask which platform he selects for his contributions to be marked against. Apparently he chooses Windows, which means that our high Linux averages aren't supported by his often generous contributions :D
Hi Cheeseness
That article looks interesting, I'm looking forward to checking it out :) 
Notch's contribution must skew that platform's standard deviation considerably cause they are also the lowest contributes by average (I only know that thanks to your stats) :)

---

### Post by Cheeseness on 2012-06-03
> **BcRich said:**
> Hi Cheeseness
That article looks interesting, I'm looking forward to checking it out :) 
Notch's contribution must skew that platform's standard deviation considerably cause they are also the lowest contributes by average (I only know that thanks to your stats) :)

Well, without knowing the distribution of values, it's not really possible to know what impact Notch's contributions would have, but if we guessed that payment values were evenly spread, we could approxmate Notch's impact by subtracting his contribution from the total amount and the dividing it by the number of Windows contributors minus one.

Based on the Humble Visualisations data current as at 2012-06-04 01:33:45 UTC, the Windows average without Notch's contribution would be $7.22, 4c lower than the $7.26 average.

Additionally, Cupcakes Nom has confirmed for me that the Humble Brony Bundle contributions are attributed to all platforms (which is nice :) ).

---

### Post by nll on 2012-06-09
Hey, Cheese, thanks for the stats and the articles!

Now with HIB V we have interesting statistics that may even indicate the broader Ubuntu adoption on the desktop.

For HIB V there has been a total of 34,112 Linux purchases as of now, 9 days after it started, and Canonical has stated that 10,000 bundles  - almost one third of all Linux purchases up to now - were  downloaded from Ubuntu Software Center just in the first 72 hours of  the bundle. I think there's no reason not to assume that this high  number of Ubuntu purchases was kept at a constant during the remaining 6  days, right? So there may have been 30,000 Ubuntu purchases by now.  Canonical will probably tell us the total number of purchases redeemed  in USC when the bundle ends, then we'll have a better picture, but I  don't believe it will be much different from this.

Therefore,  unless other distros have a much lower number of gamers than Ubuntu, we  can clearly see that Ubuntu indeed still have a massive user base in  comparison to other GNU/Linux.

---

### Post by Cheeseness on 2012-06-09
> **nll said:**
> Hey, Cheese, thanks for the stats and the articles!
My pleasure!

> I think there's no reason not to assume that this high  number of Ubuntu purchases was kept at a constant during the remaining 6  days, right?Linux purchasing patterns are really hard to predict, I think. My gut tells me that the number would probably drop off dramatically after the first couple of days - word spreads quickly amongst Linux users, and I'd imagine that with the number of Ubuntu specific news sites, user groups and Canonical/the USC itself, Ubuntu users would have to be pretty out of touch to be discovering the bundle later rather than sooner.

> So there may have been 30,000 Ubuntu purchases by now.At the moment, there are around 34,000 GNU/Linux purchasers. I'm pretty sure that the numbers will be proportionally in favour of Ubuntu users, but I doubt that there have only been 4k combined purchases across other distros. I'm only guessing though - it'll be interesting to see what the final figures look like!

> Therefore,  unless other distros have a much lower number of gamers than Ubuntu, we  can clearly see that Ubuntu indeed still have a massive user base in  comparison to other GNU/Linux.I think that would be a pretty valid interpretation, at least for the "desktop" market. I don't use Ubuntu personally, so I don't really know a lot about the USC. Is the USC usable with other Debian derivatives, do you know?

---

### Post by nll on 2012-06-10
> **Cheeseness said:**
> My gut tells me that the number would  probably drop off dramatically after the first couple of days - word  spreads quickly amongst Linux users, and I'd imagine that with the  number of Ubuntu specific news sites, user groups and Canonical/the USC  itself, Ubuntu users would have to be pretty out of touch to be  discovering the bundle later rather than sooner.

Not  every (or even most) Ubuntu user checks news daily or follows user  groups (specially non-English speaking users), while lots of users of  other distros do follow Ubuntu-specific news. Also, anyone who have ever  purchased a bundle receives emails about new bundles unless they  uncheck it on the webpage, so gamers from other distros could have been  informed pretty soon too. But yeah, if we consider just the fact that  there are much more news channels focused on Ubuntu than on other  distros, you do have a point.

> **Cheeseness said:**
> I think that would be a pretty valid  interpretation, at least for the "desktop" market. I don't use Ubuntu  personally, so I don't really know a lot about the USC. Is the USC  usable with other Debian derivatives, do you know?
Debian has an unbranded "Software Center" which I'm not sure would  work with the bundle, but you can in fact  install USC in Ubuntu  derivatives.

---

