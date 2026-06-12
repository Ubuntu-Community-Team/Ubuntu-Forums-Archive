---
title: "RAID 5 grow/change/alteration???"
date: 2009-06-06
forum: General Help
---

### Post by lordofduct on 2009-06-06
So... been using Ubuntu for a while now, since version 5 I believe as dualboot. And now for a year as my primary OS. I'm loving it, just upgraded to 9.04 64-bit. Holy SWEETNESS!


Anyways, onto my question.

I need to locate help with mdadm for a specific task, and it's something I REALLY don't want to mess up. So a description of my set up right now:

I have one machine that acts as a fileserver amongst other things (mythtv backend, webserver, thin-client remote server, and a bunch of goodies...). On it I have a RAID-5 of 3 500gig disks set up through mdadm, resulting in about 960gigs of storage space. It's at about 75% capacity now and one of the disks has failed on me, I repaired it and put the array back together, but that failure makes me weary (as it should) and I've just purchased a few new disks to replace the broken bit and maybe pull some more size out of it.

See all 3 disks are nearing 4 or 5 years of non-stop use. So I figure why not replace the entire array with 3 brand new 640gig drives. Hopefully giving me about 1.2 terrabytes and bring me down to like 55% capacity.

My thing is, I only have 4 SATA ports at my disposal to swap this array over to the new disks and end up with all my data intact and the array resized...

Is there any tutorials out there to help me?

as a round up:

3 500 gig drives one of which is failing making a RAID5
needs to be converted over to
3 640 gig drives that are brand new making a RAID5
with only 4 SATA ports at my disposal

---

### Post by fjgaude on 2009-06-07
You have to think about ways available to you to pull what you wish off.

Try reading this link and see if you get any new insight:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)

One idea is to using the "missing" feature of **mdadm** to make a two-drive raid5 and have the third slot carry the whole load of data you have. Of course you would have to buy one 1TB drive to do that, then use it as your missing drive, after you carry all of its data to the new two-drive, raid5 array you made using the third drive as "missing". Then add the big drive to the raid5 array.

Understand?

---

### Post by lordofduct on 2009-06-10
I already got this complete. The steps I took to doing it...

drives were in removable hot swappable bays, the disks were:

sdb, sdc, sdd of which each only had one partition on.

steps made:

fail sdd - # mdadm /dev/md0 --manage --fail /dev/sdd1
remove sdd from array - # mdadm /dev/md0 --manage --remove /dev/sdd1
hot swap 500gig drive from bay and place brand new 640gig drive in (if not hot swappable, shutdown, swap, and start back up)
partition entire drive unformatted
add NEW sdd1 into array - # mdadm /dev/md0 --manage --add /dev/sdd1

go play some videogames and wait for sync

once done repeat steps with sdc and sdb. After 6 hours of everything syncing and swapping...

grow the array - # mdadm /dev/md0 --grow --size=max


done... the 500 giggers are a back up just incase I failed at doing this. Which I didn't (thank God).

Downside, two nights ago the computer this was on broke or some crap. Basically it wouldn't boot anymore (I did an update and afterward kept getting a weird repeating error booting up). Instead of fixing it I took the time to just upgrade to Ubuntu 9.04 64-bit. It recognized the array right off the bat with out having to do crap! That was nice. Downside I have to install a lot of software again... I did what I needed that night, but not everything (didn't set Apache up again yet, that was just to play with anyways).

Now I'm kicking 9.04 64-bit on two machines. It's very nice. Especially on my new i7 chipe... VROOOOOOOMMMMMM! Like really, I'm a developer and a lot of software I need for my current contract is Windows/Mac only (Adobe products)... I can have both a Mac and Windows VMWare VM's open at the same time and still kick all kinds of goodness in Ubuntu with out my machine flinching the slightest.

I'm thinking that I've finally reached "compitent Linux user" level now and I'm gonna start stepping up my game some more on learning more powerful tools.

---

