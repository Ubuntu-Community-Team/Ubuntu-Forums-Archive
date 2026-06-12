---
title: "Wouldn't a &quot;Copy que&quot; for external disks  be a good thing?"
date: 2009-07-19
forum: Desktop Environments
---

### Post by Ashrael on 2009-07-19
First: I have been a computer user since 1978 and am using ubuntu since May 2005: and lovin'it, mostly...
But, when I decide to copy lots of data from several disks to my ext.hd, it takes ages to get the copy done. I do not know if there is a remedy or even what I am about to suggest, but if there is: tell me please.... The problems is that it spreads the bandwidth of the USB/FW over many copy commands. The total copy speed of, say 10 copies is about 20% lower than for one copy at a time.
Now wouldn't it be a good thing to have a que (like a print-que)for those kinds of disks, so that it will copy 10 things consecutively with no overhead? 

Any remarks, tips, etc. welcome :D

Ashrael

---

### Post by Ashrael on 2009-07-23
ANYONE? ANYTHING?

TIA!
(still eating :popcorn: )

---

### Post by Ashrael on 2009-09-15
repeat!

aaargh! no-one has any remarks/ideas/tips/etc?

---

### Post by Ashrael on 2010-01-11
no-one has anything to say about this?

strange....

---

### Post by megamania on 2010-01-11
I would use a simple script with various consecutive "rsync" commands.

This way, you would have only one copy command taking place at a time.

---

### Post by ansjov on 2013-02-18
3 years later: try krusader.
```
sudo apt-get install krusader
```

it's copy queue by the way.

---

### Post by vanadium on 2013-02-18
It is a bug in nautilus that apparently is difficult to solve:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/306630](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/306630)

---

### Post by aarons6 on 2013-02-18
as a long time linux user i wouldnt really drag and drop a bunch of files to copy from one drive to another anyway.. 

a few files its ok.. but many files id make a script or just use rsync if i was gonna do a whole drive..

---

### Post by varunendra on 2013-02-18
> **ansjov said:**
> 3 years later: try krusader.

Please don't bump threads that are more than 1 year old and haven't seen any activity in that period.

Read the [Forum Code of Conduct]("http://ubuntuforums.org/index.php?page=policy") get familiar with posting guidelines and good practices.

If the topic still seems relevant, feel free to continue it in a new thread instead.

Thank You.

Oh.. and welcome to the forums! :)

---

