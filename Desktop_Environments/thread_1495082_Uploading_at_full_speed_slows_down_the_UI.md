---
title: "Uploading at full speed slows down the UI"
date: 2010-05-27
forum: Desktop Environments
---

### Post by _christoffer on 2010-05-27
Here's a wierd problem that's left me stumped for a few days, perhaps  it's time to get advice from the community. Hope no one minds that this  ended up under Desktop Environments, but I didn't think it really fits under Networking.

I've got a fairly simple system setup - standard Ubuntu 10.4 on a Dell  workstation (Quad-core, 4Gb RAM, 2Tb hard drive). It's a workstation in the very literal sense, so every  other day or so I need to run some distributed computations on our  little computing cluster to verify updates to our products. The test  data weighs in at around 10Gb, and result data at around 1Gb, so it's not particularly large data sets. 

When synchronizing data to computing nodes, the Gnome session becomes  somewhat unresponsive, with windows greying out a few seconds seemingly  at random, and choppy mouse movements. It's not unreasonable network speeds  either, I only have a 100Mbit connection to the computing nodes, so the  data is sent at a modest 12Mbyte per second. 

I can't really begin to figure out what can be causing this. There is  obviously some kind of congestion, but why would the UI for simple  terminals and other non-networked applications behave like this?

---

