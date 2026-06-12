---
title: "Raid 1"
date: 2009-01-21
forum: General Help
---

### Post by malfist on 2009-01-21
I am getting ready to reinstall ubuntu (probably a Jaunty alpha) and I want to set up RAID this time around.
I have two disks, a 250GB and a 750GB. I only want to use 250GB of the 750GB disk because the other 500GB will be used for other purposes.

How can I do this? The RAID is provided by my motherboard (so probably fake raid) and it's a foxconn motherboard.

---

### Post by Titan8990 on 2009-01-21
Honestly, IMO, if you are looking for fault tolerance, you are probably better off just using rsync to backup your entire OS on a regular basis. 

It has always been my opinion that the only RAID worth doing is REAL hardware raid (discrete RAID controller).

---

### Post by albinootje on 2009-01-21
> **malfist said:**
> I am getting ready to reinstall ubuntu (probably a Jaunty alpha) and I want to set up RAID this time around.
I have two disks, a 250GB and a 750GB. I only want to use 250GB of the 750GB disk because the other 500GB will be used for other purposes.

How can I do this? The RAID is provided by my motherboard (so probably fake raid) and it's a foxconn motherboard.

Use the alternate or server cdrom, and go for software RAID1.

I like software RAID1. 
Good hardware Raid cards are not cheap, and if your hardware Raid card breaks on your working system in a weekend, then you have a far bigger problem than with software Raid.

---

### Post by Titan8990 on 2009-01-21
Agreed, but how do you plan to argue that the fault tolerance added by soft RAID1 surpasses a nightly rsync backup?

Both may be ideal, but I still wouldn't trust softRAID for anything.

---

### Post by albinootje on 2009-01-21
> **Titan8990 said:**
> Agreed, but how do you plan to argue that the fault tolerance added by soft RAID1 surpasses a nightly rsync backup?

Both may be ideal, but I still wouldn't trust softRAID for anything.

On one server I'm already running a nightly backup to external media.
Running another backup on an internal disk would add a much longer slowdown of the system for my users, (users which are in different timezones), than with software Raid1.
So your rsync proposal would not be an option for my setup.

---

### Post by malfist on 2009-01-21
I'm mainly looking for speed, the other 500GB is for backup for my windows and linux systems.

---

### Post by albinootje on 2009-01-21
> **malfist said:**
> I'm mainly looking for speed, the other 500GB is for backup for my windows and linux systems.

For speed you want Raid0 with at least 2 disks.
And remember that if one disk in that setup dies, you will lose everything from your Raid0 data.

---

### Post by malfist on 2009-01-21
How is RAID0 different from what I'm doing right now which is just running the / and the /home on different disks?

---

### Post by Titan8990 on 2009-01-21
There is no RAID configuration that will match the speed of a single disc. Logic tells us otherwise, numbers tell us what is correct.

When I get home tonight I will post links to articles to show that RAID0 RAID5 etc IS NOT as fast as a single drive equivalent.


If you would like to do your own research, you will find that this is very true.

Also, RAID0 does the opposite of fault tolerance. It actually makes it fault intolerant.

---

### Post by malfist on 2009-01-21
So what I'm doing now it actually faster than RAID0/1?

---

### Post by malfist on 2009-01-21
That doesn't make any sense. Can you post some links?

---

### Post by albinootje on 2009-01-21
> **malfist said:**
> How is RAID0 different from what I'm doing right now which is just running the / and the /home on different disks?

See here : 
[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks#Standard_levels](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks#Standard_levels)

Raid0 uses two or more disks and divides the data over the disk.
With your current situation with / and /home on two separated disk you would not gain much speed.
You should ask yourself however whether you want Raid0.
I can imagine that gamers want Raid0, and perhaps people with some application-server.

---

### Post by malfist on 2009-01-21
I was thinking of RAID1 because most of activities done require more reading than writing...

---

### Post by Titan8990 on 2009-01-21
First google result of "RAID0 benchmarks"

[http://tweakers.net/reviews/515](http://tweakers.net/reviews/515)

---

### Post by malfist on 2009-01-21
Those are all really small transfers though. I don't think I saw a test that performed more than 32KB which is really biased. That can be done in the buffer of most drives...

---

### Post by Titan8990 on 2009-01-21
And where are your numbers to prove me wrong?

Around 8months ago, I had this same argument only I was on your side, arguing your point of view. This quickly changed when I was unable to find benchmarks that showed RAID0 being faster than a single drive.

Do some research, and lets see your numbers that prove me wrong.

---

### Post by malfist on 2009-01-21
Well, techincally the burden of proof is on you because you're the one claiming something but lets not go there. The problem is, most benchmarks don't have a single drive comparison.

---

### Post by malfist on 2009-01-22
Okay, I've done my homework

[http://faq.storagereview.com/tiki-index.php?page=SingleDriveVsRaid0]("http://faq.storagereview.com/tiki-index.php?page=SingleDriveVsRaid0")
[http://www.ocforums.com/showthread.php?t=310250]("http://www.ocforums.com/showthread.php?t=310250")
[http://anandtech.com/storage/showdoc.aspx?i=2974&p=7]("http://anandtech.com/storage/showdoc.aspx?i=2974&p=7")

---

### Post by Titan8990 on 2009-01-22
Alright, confirmed, RAID0 will increase performance in select application. Is it worth the risk?

---

### Post by malfist on 2009-01-22
I am still backing everything up so, yes. I actually have three harddrives. 200GB for Windows, 250GB runs linux, and 750GB is backup. All three are fully encrypted. I will still have plenty of backup space. I think I will do it.

---

### Post by Titan8990 on 2009-01-22
I still disagree with it being worth it but it is you decision to make.

Good luck.

---

### Post by malfist on 2009-01-22
I'm puzzled. I get the speed boost, and I still have everything backed up (I use rsync). Would you tell me why you think it's not worth it?

---

### Post by Titan8990 on 2009-01-22
Even those articles showed that the speed increase only occurs in select applications. I don't use any of the applications shown specifically take advantage of striping. 

I would rather not have to reinstall my OS every so often because my guaranteed to fail RAID crapped out. 


And lastly I plain don't believe in fakeRAID or softRAID. 


You also need to understand that softRAID and fakeRAID takes extra CPU power that discrete cards do not.


But again, it is your choice. Do your thing and learn from your experiences.

---

### Post by malfist on 2009-01-22
Oh, I have CPU clock cycles to spare, I'm running a quad core ;) AMD Phenom 9850 Black 2.5GHz oced to 2.9GHz

---

### Post by malfist on 2009-01-22
I think guaranteed to fail is the wrong phrase. Both drives will fail at the same rate they would normally. Just when one goes, the other one will be corrupt. However I'm still backing up my hard drives so I don't really see the issue? Neither harddrive is more than 1.5 years old. I should have several more years before they fail, and I plan on adding another 750GB sometime this semester.

---

### Post by Titan8990 on 2009-01-22
RAID also has issues with corrupt files. Keeping a regular backup is a good practice and will prevent you from having a disaster but you will have problems eventually nonetheless.

You are at even more of a risk using a heterogeneous drives. Prior to articles such as this one it was often said that a heterogeneous RAID array would not even work: [http://www.tomshardware.com/reviews/HETEROGENEOUS-RAID-ARRAYS-WORK,1789.html](http://www.tomshardware.com/reviews/HETEROGENEOUS-RAID-ARRAYS-WORK,1789.html)

---

### Post by malfist on 2009-01-22
Thank you for the information. I will definatly do some more reasearch before implementing RAID, but at the moment I think I will still do it.

---

