---
title: "raid1 or raid5 for server plz hlp thx"
date: 2009-01-13
forum: General Help
---

### Post by splitlenz on 2009-01-13
Not sure exactly where to put this, so i put it in general. 

I have a computer with these specs.
Intel Core2Duo, 2x 2.66+ GHz, 
3 MB L2 - FSB 1066 MHz, 
2GB DDR2 RAM, 
64-bit architecture, 
4x 1500 GB SATA2 HDD 

Ubuntu Desktop 8.04 running FreeNX,
Wine & uTorrent
perhaps webserver also, apache,php
Approximately 6 people will have access to the pc, usually remotely.

Will Software RAID5 be a performance issue or will it handle fine? Is hardware RAID1 better? If so by how much? 

sidenote: should i upgrade to 8.10? 

Thank you for the help.

---

### Post by LoneWolfJack on 2009-01-13
nobody will be able to make more than an educated guess unless you specify how many people will be logged in at once, how much bandwidth they will use, etc.

however, assuming you don't want to spend the 500 bucks on a hardware raid controller, you can only go with software raid. don't let yourself be fooled by 50 buck raid 1 controllers. I have yet to see one that is more than a raid extension card (so software raid again). 

in terms of the performance impact of software raid on the CPU, raid 5 will be WAY worse than raid 1.

---

### Post by dcstar on 2009-01-13
> **splitlenz said:**
> 
..........
Will Software RAID5 be a performance issue or will it handle fine? Is hardware RAID1 better? If so by how much? 


With 4 drives you can have 2 RAID-1 arrays (one for system & data, and another for data), so if you have a drive failure on either then they are both separated and wont affect each other - it's up to how "available" you want your system to be.

I have had poor experiences with the "Fakeraid" hardware RAID that is built into some motherboards, the control is taken away from the OS and that can cause performance issues at times.

You may want to experiment with a few installs of the different configurations and see what performs well enough for you, the different install times may give you an indication of the performance differences versus resilience.

---

### Post by Splitting.Heads on 2009-01-14
splitlenz posted for me since I didn't get an activation email before :)

Maximum 6 users logged in at once at any given time depending which RAID setup I go for.  I am really not keen on RAID 0 and losing everything if a single disk fails, especially since someone else with the same box lost a HDD within 3 days of getting his server.

Bandwidth the users logged in will use will vary it, very little being uploaded to the box, most of it download traffic to home PC's of the users or peers in utorrent.

They don't offer hardware RAID by the sound of it.  RAID1 cuts the storage space in half which drops amount of users and raises the cost which I'd like to avoid.

My primary interest is maximizing storage space at a reasonable cost benefit without killing performance.  As mentioned in the OP it's going to pretty much be wine, uTorrent with webUI and FreeNX up to 6 users at one time maximum, very rare would they all login at the same time.

---

### Post by electrogeist on 2009-01-14
I highly recommend against RAID 5 with drives that large (1.5TB) It will take forever + a day to rebuild the array when a drive fails... I have seen reports of people losing another drive in the meantime.  Additionally, being 1.5TB they are probably the Seagates with above normal failure rates.  This would be asking for trouble.

Consider RAID 10, mirrored for redundancy and striped for speed, which will net you a 3TB array.  And consider a hot spare.
 
 
Slashdot:  Seagate Acknowledges Problems With 1.5-TB HDD
[http://hardware.slashdot.org/article.pl?sid=08/11/11/2125227](http://hardware.slashdot.org/article.pl?sid=08/11/11/2125227)
(discussions of RAID in the comments too)

---

### Post by stefangr1 on 2009-01-14
I think you could have some performance issues with raid-5, basically when someone on the network is copying large files. Read performance is generally good.

For downtime the choice between raid1 and raid5 doesn't matter, both can run with one disk failing or detached. You should never use the fake raid controller of your motherboard, but in stead use the alternate install cd to get a linux software array (but you probably already figured that out). I have tried rebuilding an array only in vmware, and I think you should expect 3-5 hours to rebuild. Would that overstress the disk array such that another disk breaks?

---

### Post by Splitting.Heads on 2009-01-15
Yeah the downtime doesn't matter if I get the data back, it's not a mission critical server by any means.  It would have 5-6 users max across the planet so multiple logins will be rare let alone all logged in at the same time.

It's just the day to day use of it I'm worried about being too slow, like 20+ seconds to load a torrent in webUI or something.  I've got dozens of answers on this nobody seems to be able to agree.

---

### Post by LoneWolfJack on 2009-01-15
ok, I'll try a pretty straight forward answer then:

worrying about performance? -> raid 0
need reliability? -> raid 1
need reliability but want as much speed as you can get at the expense of capacity? -> raid 10
want to balance reliability and performance at low cost and you can live with a high CPU load? -> raid 5

not happy with these? buy a hardware raid controller, get 4 more drives and set up a raid 60, the king of all raid levels.

note: no (and absolutely no) raid level is an excuse for not pulling backups.

---

### Post by igknighted on 2009-01-15
> **LoneWolfJack said:**
> note: no (and absolutely no) raid level is an excuse for not pulling backups.

+1

great point, and sadly often overlooked.  I would say catastrophic hardware failure (PSU blowup, power surge, etc.) are almost more likely than a random disk failure, so chances are good that more than one disk would be damaged, making all the raid in the world rather meaningless.

---

### Post by Splitting.Heads on 2009-01-15
Yeah complete backup will be up to each user, there's plenty of web-based storage services to choose from to do that.  I'm more interested about the high CPU load which is turning me off the RAID5 atm.

Considering a trial run for a few weeks to see how it goes and if it sucks I'll try something else.  Too bad they use garbage Seagate drives.

---

