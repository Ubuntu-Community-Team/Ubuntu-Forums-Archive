---
title: "Server specs"
date: 2011-10-04
forum: Gaming &amp; Leisure
---

### Post by Jagoly on 2011-10-04
Just a few questions about what sort of specs you would need for a server of the following specs. Just to clear up, I doubt I'll ever build this particular server. I do intend to build this sort of server, but that won't be for another 1-2 years. But I'm just curious as to what would be necessary if it were built with today's components. And at this point no budget, just what's required for the task.

So if I wanted to:
- Host two minecraft servers, probably virtual, one public (with 30+ players, and one private with 10-20 players.
- host a mid-sized (6 TB) private file server for me and my family. Decent performance is necessary.
- basic apache duties. No idea what I'd host, but who cares, it'd be something. Not intensive whatever it would be.
- Media streaming to local/remote machines. My local network's streaming devices at the moment are PS3's, but by the time I'd build this, I'd have a HTPC(s). I'd probably get it to encode the stuff too.

At the moment, my guess for specs would be:
- Core i5 2500 or whatever the cheapest quad core XEON is, depending on how I set up the networking on the VMs.
- 5 x 2TB 5400rpm HDDs in raid 6
- 60gb SSD
- some sort of RAID card, not sure how SAS and stuff works
- A good and fast ethernet card, probably dual outputs, teamed for main OS. Running the VM's on the integrated LAN. My current internet connection sucks (3G gateway), but by the time this is built I'll have ADSL2+ (or if I'm lucky a fibre for the NBN).
- Decent mATX mobo in a good mATX case, my current favourite is the Fractal Design R3
- 8gb of decent non-overclocking ram.
- 400-500 watt gold certified PSU

What would other people use? Of course this machine would run the server version of my favourite OS :-)

---

### Post by mastablasta on 2011-10-04
i would use something so powerfull. since server runs via command line. it doesn't have any GPU.... Celeron might be handling stuff just fine. but then again depends how many users will attach to it.
 
to give you some comparison - ive' seen dedicated server for Wolfenstein enemy territory using 400 something Mhz processor and 256 RAM. remember server doesn't need so much power and all that.especially if you are not performing some really demanding functions and plenty of them. and plenty users that connect to it so it has to handle them. but if you have the budget, then just go for it.
 
8GB ram, ok how are oyu plannign to fill them up? with what?
 
maybe media streaming can use the power but game server? file sharing? apache? they dont' take as much...

---

### Post by Drenriza on 2011-10-04
Well.

For data security you would need a RAID5 system along with a backup system of some sort.
Also, if you get the server, get your network in order to direct the traffic in the most optimal way.
Get some Cisco equipment at E-bay or something.

Also i would go with a AMD server CPU instead. Probably the opteron third-generation series.
But comparing benchmarks before this is a good idea. But also to thinks of one power-needs (watt) and economy is a good idea.

EDIT. Refreshed my RAID6 and remember it has a double parity, which means you lose 50% of your system disk space with 4 disks.
So in a 4 disk array with for example a total of 4TB you have 2TB available for use and 2TB for backup of parity.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by Jagoly on 2011-10-04
> **mastablasta said:**
> i would use something so powerfull. since server runs via command line. it doesn't have any GPU.... Celeron might be handling stuff just fine. but then again depends how many users will attach to it.
 
to give you some comparison - ive' seen dedicated server for Wolfenstein enemy territory using 400 something Mhz processor and 256 RAM. remember server doesn't need so much power and all that.especially if you are not performing some really demanding functions and plenty of them. and plenty users that connect to it so it has to handle them. but if you have the budget, then just go for it.
 
8GB ram, ok how are oyu plannign to fill them up? with what?
 
maybe media streaming can use the power but game server? file sharing? apache? they dont' take as much...

Minecraft server is very demanding. When there is a lot going on, on my microserver anyway, ram usage easily passes 1gb with a less then 10 players. And when they all are throwing TNT at each other, the 2.5GHZ 2100t runs at 100% and the server still lags ridiculously. And I wanted to run two.

That, plus media serving (to my whole family, not one person).

I already have a small server I built a few months ago. mini-itx, 2x320gb WD scorpio blue, i3-2100t 2.5ghz, 2gb Ram, and i have tried doing all of these things on it, it can't even come close.

So I don't think a Celeron would cut it.

And remember, at this point this is all theoretical :-)

@Drenriza: i know how raid levels work ;-)
I'm Happy to lose four TB, 6TB is plenty. Double parity seems more important, unless you dont think it's nescecary.

---

### Post by mastablasta on 2011-10-04
yeha i don't think minecraft is really optimised yet. i've noticed LAG even on single player... can't imagine MP games on it....
 
me i plan to get something small (when and if i have the money). perhaps along the lines of your current build.

---

### Post by Drenriza on 2011-10-04
> **Jagoly said:**
> So I don't think a Celeron would cut it.
And remember, at this point this is all theoretical :-)

Thus why i suggested a more powerful processor. But still network is important.
It's also cool to let your family stream stuff from one house to another, which can be done over VPN, so it looks like your all on the same LAN.

> **Jagoly said:**
> 
@Drenriza: i know how raid levels work ;-)
I'm Happy to lose four TB, 6TB is plenty. Double parity seems more important, unless you dont think it's nescecary.
Just an info :p

---

### Post by a2j on 2011-10-04
good specs, sounds like a plan.
I do similar staff to what you've described. Recently added more ram and replacing dual core C2D with quad. no ssd, just raid6 with 4 green WD drives. runs great. minecraft, file/web/ftp/mysql server, online photo album, etc...

---

