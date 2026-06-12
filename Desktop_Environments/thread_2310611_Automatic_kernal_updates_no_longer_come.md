---
title: "Automatic kernal updates no longer come"
date: 2016-01-20
forum: Desktop Environments
---

### Post by Wadcutter on 2016-01-20
I'm baffled by the Linux kernals.
 

 My wife and I both run Ubuntu 12.04 on desktop computers. We both get regular OS, application and security updates, but my computer also receives automatic Linux kernal updates, but her computer has stopped receiving them.  I'm currently at 3.2.0.98 while she has stalled at 3.2.0.94.
 

 Even before her kernal updates (upgrades?) stopped coming, she always lagged receiving them by several days behind my receipt of them. Don't know why.
 

 I'm a bit wary of messing with kernals, so I would like to find some solid info on how to get her back on track for receiving the updates regularly before I start tweaking things. She did receive 3.2.0.95 a few months ago, but it was somehow corrupted and her graphics were out of whack. I restored her to 3.2.0.94 and that is where she has been ever since.


Searching other posts for info before adding my request make me wonder if I should be careful about what I am asking for. There seems to be a history of all kinds of mischief being caused by the automatic kernal updates. Maybe I should leave her computer alone (since it's working fine) and instead try to disable the kernal updates on mine? Dunno.

 

 Thank you.

---

### Post by grahammechanical on 2016-01-20
If it ain't broke , don't fix it. Is good advice.

Have you ever heard of phased updates? This explains it.

[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

I have 2 installs of 16.04 development version on the same machine and they both have a different kernel version. It is strange but true. 

> Giving an entirely new version of any widely used  software program to our entire user base all at once is unnecessarily  fraught with peril.


Instead,  let's employ a phased update strategy wherein we provide the updated  software to an ever-expanding set of random users. This pool of users  will be grown as our confidence of that software update grows, fed by  realtime information from the crash database and other potential  sources. 


This process will be developed in tandem with the efforts to increase testing of packages in -proposed so that we have more confidence in the updates we are pushing out. This process will add to that the ability to pull an update before a large number of users encounter it.

If a kernel upgrade seems to break the system we can go into Advanced options for Ubuntu at the Grub boot menu and select an previous kernel. And then  there might be an update a few days later that fixes the problem. There is no need to remove the new kernel.

If you run

```
sudo apt-get update
sudo apt-get upgrade
```

You may see a list of packages being held back. It may include a kernel upgrade. These packages are held back for a reason but they will be installed eventually.

Regards

---

### Post by Wadcutter on 2016-01-22
Thanks for your time to explain things. It makes perfect sense. Something interrupted the download of kernal ver 95 and, I believe, corrupted  it. The next time she booted, the graphics were frozen into a very low resolution. I did what you mention by going back into Grub and rolling her back to ver 94. I did, however, delete 95 because I though it now had bugs in it caused by the interrupted download. No further updates have come since then (Approx November 20, 2015). i tried what you suggested above, but it only needed to upgrade rsync--no mention of kernals.  I think we are OK with things the way they are. We will probably both be upgrading to a more recent version of Ubuntu soon and that will probably take care of this (and create a whole host of new issues to deal with) Thanks, again.

---

