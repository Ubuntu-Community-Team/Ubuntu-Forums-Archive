---
title: "Settings up Raid 0 on ubuntu , mounting commands?"
date: 2009-02-19
forum: General Help
---

### Post by Espryon on 2009-02-19
Im running Hardy Heron

anyone know the steps to create a raid 0 array?

I want to Make a raid-0 with two Samsung 500 Gig Drives

---

### Post by oiad on 2009-02-19
If you are doing a fresh install use the ubuntu alternative cd.  When you get to the partitioner create the partition on each drive and set the 'use as' to 'physical volume for raid'.  Then you go to the top and select configure software raid and follow the on screen instructions.(picking raid 0 and the partitions involved)  
  You will want to have each of your partitions (/,/home/) whichever you do as their own partition set to physical volume for raid.  Make sure you set the / partition bootable flag.

This site has picks of all of the screens in the ubuntu alt cd raid setup.  They are doing a raid 1 but just change those settings to raid 0.

[http://kuparinen.org/martti/comp/ubuntu/en/raid.html]("http://kuparinen.org/martti/comp/ubuntu/en/raid.html")

---

