---
title: "Help me find Dell boxes!"
date: 2012-05-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pot_roast on 2012-05-18
I'm looking to replace an old PowerEdge 2450 that I have in a data center. It's a fairly low traffic web/email/ftp server.

I'm also looking for a Dell tower box to put at home on my FIOS connection so I can put a few 2-3 TB drives in it and use it for a home media/home network server. 

Ideally I'm looking for particular model numbers that I can find used that support Ubuntu very well. Used boxes that are maybe 1-2 years old have generally worked well for me in the past.
 
Hoping to find Ubuntu friendly RAID models as well. For example, the "PowerEdge 2650 with the PERC 5 has worked well for me." Once I have some very Ubuntu friendly model numbers, I can add RAM and stuff from there. 

I'd prefer a functional RAID card for the rackmount box (like the PERC series) and am ok with SATA drives. The home box should mostly be bulk storage, so I think I should be able to get away with software RAID only.

This is important to me because my old 2450 is an example - I cannot perform a graceful reboot of the machine and always have to have the data center folks reset it for me. I did *not* have this problem with a dearly departed 2650, though. I'm in another country right now and am going to be ordering these boxes to be shipped to my home in the US where a not-so-linux savvy friend of mine will be setting them up with me during a Skype video session.

Please, no "wtf build your own" comments. Thanks. :-)

---

### Post by LHammonds on 2012-07-24
[This is the page]("http://www.ubuntu.com/certification/server/make/Dell/") that shows what Dell servers are certified to work with Ubuntu server.

I have a couple of 2950 servers (with PERC 6), several 2850 (with PERC 4) and a ton of 2650 servers (with PERC 3) that are not being used since we converted most physical servers to virtual servers on an IBM BladeCenter.  I have a variety of other miscellaneous Dell servers but none of them have a PERC 5 controller.

I was curious to see if I can get one of the 2650 servers to work but because the 2950 servers were listed in the link above, I will probably start off my test with one of those servers.  I am going to see if I can build a server to host virtual servers much like my existing VMware ESXi 4.1 setup.

**EDIT:** Ubuntu Server 12.04 LTS (64-bit) installed just as easy at it could be on my Dell PowerEdge 2950 server (12 GB RAM, 5 73 GB drives in RAID 5 which gave 300 GB)

LHammonds

---

### Post by pot_roast on 2012-07-24
You know, this is the first time that I have seen that link? None of my Google searches brought it up until I threw in the word "certified." 

Thanks!

---

### Post by dfrandin on 2012-08-12
I'd say eBay is a good choice.. I've picked up a few Dell PE servers from various sellers there over the years, all the way from an old PE750 that I bought for $65, with maxed out 4GB of RAM and 2 250GB SATA with a CERC SATA RAID controller. It still runs at the house as a headless virtualbox server with a Windows 2003 and a 2008 vm running on it, local caching dns, several samba shares as a backup location for the home systems. Runs Ubuntu 10.04 just fine.. Short answer: try eBay..

HTH
Dave

---

### Post by Tobeus on 2012-08-13
Don't forget to check out pacificgeek.com when you are looking for the old server stuff.  I keep an eye on them for surplus server stuffs and have found several decent deals.  Probably not quite as good as the occasional gem on ebay, but if you don't mind spending a little more (still awesome used prices) for getting something you know is going to work, they do a pretty good job.

Whether they have anything that is on the known-good hardware list is up in the air though.  It all depends on what they have, so cross reference them both.

Good luck, and I hope you find a decent server!

-Tobeus

Forgot to mention the dell boxes.  I use propertyroom.com for buying dell towers.  They usually have something decent every so often.  They are police/government/business surplus, and they get stuff all the time.  I've purchased 4 Dell Optiplexes with decent specs for about $60-$80 / box (no hard drives though).  Hard to beat those prices, and that was including shipping.  Good luck!

---

