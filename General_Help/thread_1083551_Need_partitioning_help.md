---
title: "Need partitioning help"
date: 2009-03-01
forum: General Help
---

### Post by Admiral Yi on 2009-03-01
Hello,
Just upgraded my computer and im trying to install Ubuntu on my new 1TB hard drive (SATA, if its important). When I start installing, it gets to the partitioner but then doesn't do anything. When it hit forward it says I need to select a root partition. I can't do this as all the buttons are greyed out. 

I have a live CD of Gparted, so I can create partitions with that. I knwo I need a root, swap and one other partition, but I don't know what format. Swap probably uses the 'linux-swap' format, but I don't have a clue with the others. Any one able to help?

Also, what size do I need each partition to be?

---

### Post by x33a on 2009-03-01
use ext3 format. size depends on your choice. for root 10-15 gb would be good enough.

---

### Post by Admiral Yi on 2009-03-01
Hello,
Just upgraded my computer and i'm trying to install Ubuntu on my new 1TB hard drive (SATA, if its important). When I start installing, it gets to the partitioner but then doesn't do anything. When it hit forward it says I need to select a root partition. I can't do this as all the buttons are greyed out. I don't get an option to use guided or manual installs. When I had a USB it got the guided/manual installation page but it wanted to install to my USB (which I don't want ;)). Seems like its not reading my hard drive. I do have a second one in there (also SATA, 80GB) but that has windows on it and is unplugged at the mo (so I don't accidentally partition that). I tried it with that one plugged in, but it doesn't make a difference. When i had my previous computer (with Ubuntu installed under Wubi) the hard drive would come up as '80GB media' under 'places'.

I have a live CD of Gparted, so I can create partitions with that. Gparted does seem to recognize both my hard drives. I know I need a root, swap and one other partition, but I don't know what format. Swap probably uses the 'linux-swap' format, but I don't have a clue with the others. 

Any one able to help me?

---

### Post by handy on 2009-03-01
Yes, I think using GParted on it's own bootable CD/DVD, or even the GParted in the Gnome Menu of the Ubuntu LiveCD should be fine.

There will be an option for /swap in GParted, as far as your choice for other file systems is concerned, there are on going arguments all over the internet on that subject.

I personally use JFS, if you are particularly concerned on the topic have a quick search here or on the internet & you will gather comparative info on the various file systems & there strengths & weaknesses.

Here are a couple of links that may help you out:

[I][U][http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)[/U][/I]

---

