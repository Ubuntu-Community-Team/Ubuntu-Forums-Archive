---
title: "Partitioning"
date: 2009-06-18
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-06-18
As of right now I have a tri boot. Win, pclinuxos and ubuntu. Pclos is on it's own  hdd and win and ubuntu is on the primary slave. I have a hdd on the secondary master where I keep al my vid's music, pic's etc, etc...There is a primary part and extended part. I was thinking about adding another system on this hdd. I the partitioning is a lil "unorginized" right now. I have 4 ext3 fs 2 swaps and 2 fat. The one fat I [DO NOT] wanna loose. So I'm a lil nearvous about messing with this hdd. Just wanna get some insight on what I can do with the other partitions, as far as repartitioning and installing, or mayby leaving it as is and installing maybe even a (couple) more distros.

---

### Post by Amilo1718 on 2009-06-18
gparted?

---

### Post by Feelin_froggy8877 on 2009-06-18
Well yeah.. but not sure what can be repartitined without effecting the "storage" part. Or if I even can.

---

### Post by Amilo1718 on 2009-06-18
but you want to boot up 4 different OS's...
kinda strange (imho)just asking... why so many?

---

### Post by Feelin_froggy8877 on 2009-06-18
Boredom really, And  cause I can :). Was thinking about utilizeing all 4 ext3's But would really like to repart them into 1. Can I do that without effecting my storage?

---

### Post by merlinus on 2009-06-18
You can use gparted to combine them into one larger partition.  This will of course change your partition numbering, and may require a bit of tweaking of various files such as /etc/fstab.

---

### Post by Feelin_froggy8877 on 2009-06-18
Do I have to delete the ext3's and the swaps then create the /home /root and swap?, or is there another way? I know a bit about disk partitioning, But I am still, like I said a lil nervous about messing with this hdd, alot there I don't wanna lose.

---

### Post by merlinus on 2009-06-18
I am a bit confused.  Are you wanting to reinstall ubuntu?  I thought you wanted to combine the small ext3 partitions into one larger one.

---

### Post by Feelin_froggy8877 on 2009-06-18
The partitions I want to combine are on a hdd that I keep pic's, music, vid's etc on.  I just wanna know If I can repartition it without Loosing my /dev/sdc9/storage. All these partitions are in an extended partition of the drive.

---

### Post by merlinus on 2009-06-18
I notice that you also have two swap partiitions.  You can certainly combine sdc5, 6, and 7 into one, but you would have to move sdc9 before you could add sdc10 to them.

As long as you do not format sdc9 you will be okay, but remember that moving and combining partitions can sometimes create problems.  It is always advisable to back up critical data anyway.

---

### Post by Feelin_froggy8877 on 2009-06-19
Ok. So, in theory, As long as I stay away from formatting, I can combine theses without loosing any data, I'm assuming I would use the "resize/move"? I've done alot of partitioning, but never messed w/ resizing/moving. I'm really unsure about how to go about this. Can you try to explain in a little more detail?

---

### Post by merlinus on 2009-06-19
The gparted website has screenshots that may be useful.  And yes, resize and/or move is what you are wanting.

---

### Post by Feelin_froggy8877 on 2009-06-19
Alrighty, I'll check it out. Thanx for everything :)

---

### Post by merlinus on 2009-06-19
Good luck, and let us know how it works out.

---

### Post by Feelin_froggy8877 on 2009-06-21
Well I been reading through alot of tutorials, But when it comes down to it, I'm too chicken @#$% to try this without being able to backup  almost 100 gigs of time and goodies. So untill I get a dvd burner or an external hdd Ima leave this 1 alone. Thanx for everything though. :)

---

### Post by Feelin_froggy8877 on 2009-06-25
Turns out I can just delete the partitions I didn't want in the extended part. And just create 1 larger partition. Was still a bit nervous about it, but I just grited my teeth and clicked apply. haha. Here's what it looks like now...

---

