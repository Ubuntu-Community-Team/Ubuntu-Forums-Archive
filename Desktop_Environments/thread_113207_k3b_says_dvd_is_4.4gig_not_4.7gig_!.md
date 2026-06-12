---
title: "k3b says dvd is 4.4gig not 4.7gig !?"
date: 2006-01-05
forum: Desktop Environments
---

### Post by cobelloy on 2006-01-05
Hi there, 
I have wine + dvd shrink to legally back up my dvd's, but k3b keeps saying that my blank DVDs are "sequential media" and that they are only 4.4G, I have recently re-installed my system, but - I have used k3b to back up a dvd movie already and it worked just fine (I have watched it - and it works fine), the only thing that has changed is the new installation of wine + dvd shrink (and some games aswell) - the first DVD I burned with k3b was from files generated using dvd shrink under windows. Dvd shrink is working just fine. I have tried two different brands of dvd's - a plain generic brand and some sony ones, both come up as 4.4G even though I have selected 4.7G size media. The only other odd thing I have noticed is a set of numbers that come up during boot that says the boot sector record is not the same as the backup copy - and then a list of numbers indicating conflicting sectors or something, the system boots fine to both ubuntu and winXP tho. I really don't understand.

---

### Post by gingermark on 2006-01-06
Your DVDs are 4.4GB. They are only 4.7 GB if you say 1000MB = 1GB, which it isn't. It's 1024 MB = 1 GB. and 1024 KB = 1MB.

Basically the real world has struggled with this and figured "a 1000 is close enough".

Sorry.

---

### Post by frodon on 2006-01-06
I agree, i alway seen my DVDs as 4.4Go disks with my computer whereas it's printed 4.7Go on the DVDs ;)

---

### Post by cobelloy on 2006-01-06
so then that would mean that dvd shrink is not working right with wine afterall? (since it all went trouble free when I used windows to copy then linux to burn?)

perhaps I need to check the settings in dvd shrink?

how annoying tho! all the dvd's have 4.7G printed on them - good work sony... (and all the others too)

---

### Post by bugunku on 2006-01-19
[QUOTE=gingermark]Your DVDs are 4.4GB. They are only 4.7 GB if you say 1000MB = 1GB, which it isn't.[/QUOTE]
You still got it wrong. DVDs are only 4.7 GB if you say 1,000,000 bytes = 1 GB. 4,700,000 bytes  ~=  4,590 [KiB]("http://en.wikipedia.org/wiki/KiB") (what is normally but inaccurately called "kilobytes", KB)  ~=  4.48 [GiB]("http://en.wikipedia.org/wiki/GiB") (GB).
Strangely, Nero won't let you burn 4590 KiB if you have overburning disabled, so I guess the real capacity is still a bit lower.

---

### Post by brucewagner on 2008-01-10
Well, then...

**Here's a good question...**

WHY / HOW do the manufacturer's get away with printing 4.7GB right on the front of the blank media....   when it is obviously NOT true....  no matter how you calculate it....?!?

---

### Post by karusho on 2008-01-10
Actually, the manufacturers are right when they print 4.7GB on the disks.  Long ago, there was a split.
Kilobyte (KB), megabyte (MB), and gigabyte (GB) were designated 1000 bytes, 1 million bytes, and 1 billion bytes respectively, as kilo=1000, mega = 1 million, giga = 1 billion
For computer minded people, they created Kibibyte (KiB), Mebibyte (MiB) and Gibibyte (GiB),meaning 1024, 1048576, and 1073741824 respectively.

So when the manufacturers print 4.7 GB, they are technically correct.

It's us who are incorrect.  Most computer people refer to KB, MB, and GB as if they meant KiB, MiB, and GiB.  This is the same with programs like k3b, etc.

Boggles your mind, doesn't it?

---

### Post by brucewagner on 2008-01-10
Wow.

That's worse than the metric system versus the imperial system...

---

### Post by karusho on 2008-01-10
See here for more info:

[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)

---

### Post by brucewagner on 2008-01-10
In our lifetimes, new machines will come with a 2.5 yottabyte storage capacity.

That's when the yottabyte / yobibyte difference is really going to upset people....

at about a 21% difference between the two....

---

