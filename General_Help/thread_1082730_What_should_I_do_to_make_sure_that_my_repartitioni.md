---
title: "What should I do to make sure that my repartitioning is going to be safe?"
date: 2009-02-28
forum: General Help
---

### Post by wersdaluv on 2009-02-28
I have a partition for my /home, Ubuntu root, Vista, and a light distro. I want to have another space for another OS for testing purposes and I'm not considering virtualization for it. I need about 11 or more gigs. My /home partition has 6 free gigs, my root has 5 free gigs, and my Vista has 1 free gb. I think, I'll just free up space from my home partition because I can't afford to make my Vista and Ubuntu partitions smaller. I can free up 20gb of space from my /home partition if I'm desperate so it would not be a problem.

It's just that, my /home partition is 113gb big with 107gb used.That's a huge amount of personal data. I don't have an external HD or any other storage to backup it to. My most important files are backed up by Dropbox but that's just 1gb of data. Losing the 112gb would still be very painful. 

How safe is resizing my partitions? What can I do to make sure that my data will be preserved? Also, when Jaunty comes out, I want my /home partition to be ext4. How do I prepare for that?

---

### Post by dbbolton on 2009-02-28
> **wersdaluv said:**
> I have a partition for my /home, Ubuntu root, Vista, and a light distro. I want to have another space for another OS for testing purposes and I'm not considering virtualization for it. I need about 11 or more gigs. My /home partition has 6 free gigs, my root has 5 free gigs, and my Vista has 1 free gb. I think, I'll just free up space from my home partition because I can't afford to make my Vista and Ubuntu partitions smaller. I can free up 20gb of space from my /home partition if I'm desperate so it would not be a problem.

It's just that, my /home partition is 113gb big with 107gb used.That's a huge amount of personal data. I don't have an external HD or any other storage to backup it to. My most important files are backed up by Dropbox but that's just 1gb of data. Losing the 112gb would still be very painful. 

How safe is resizing my partitions? What can I do to make sure that my data will be preserved? Also, when Jaunty comes out, I want my /home partition to be ext4. How do I prepare for that?
I could be wrong on this, but I don't think you can have more than 4 primary partitions on one hard drive. 

Also, I don't think you can format a partition to a different filesystem without destroying all the data on it (unless there is some exception between ext3 and 4).

That being said, resizing any partition is at best risky. I have lost data resizing an ext3 partition in the past. If you are really concerned about losing data on your hard drive, I'd recommend not touching it.

---

### Post by avrilrox on 2009-02-28
I've personally never lost any data while resizing partitions. I never backup my data but I'm very careful to click the right choices.

I've resized EXT3 and NTFS partitions without any data loss.

I do admit it's a bit risky though.

---

### Post by dmizer on 2009-02-28
> **wersdaluv said:**
> I have a partition for my /home, Ubuntu root, Vista, and a light distro. I want to have another space for another OS for testing purposes and I'm not considering virtualization for it. I need about 11 or more gigs. My /home partition has 6 free gigs, my root has 5 free gigs, and my Vista has 1 free gb. I think, I'll just free up space from my home partition because I can't afford to make my Vista and Ubuntu partitions smaller. I can free up 20gb of space from my /home partition if I'm desperate so it would not be a problem.

It's just that, my /home partition is 113gb big with 107gb used.That's a huge amount of personal data. I don't have an external HD or any other storage to backup it to. My most important files are backed up by Dropbox but that's just 1gb of data. Losing the 112gb would still be very painful. 

How safe is resizing my partitions? What can I do to make sure that my data will be preserved? Also, when Jaunty comes out, I want my /home partition to be ext4. How do I prepare for that?

If you want to be assured that your data won't be lost, then you need backups. If you can't make backups due to size concerns, then I strongly suggest you give SERIOUS thought to how badly you REALLY need that extra space.

If you can't afford to lose your data and you can't make backups, don't fiddle with your partitions.

Hard drives are cheap, you could get a bigger disk and use dd to make a copy, or [hdclone]("http://www.miray.de/products/sat.hdclone.html") makes a fantastic click interface 1:1 drive copy (I use it very frequently).

Your drive is so full at this point that you're probably suffering some speed loss as a result as well. It's not good to run drives at 99% capacity, they're much more prone to failure that way.

---

### Post by avrilrox on 2009-02-28
Can't you backup your data on DVD's? Or maybe get a friend to back up your data? I have two hdds, 500gb and 320gb and i often backup my friends' data.


I'd totally do it for you, but you're just too far away.

---

### Post by wersdaluv on 2009-02-28
Thanks for the suggestions. I have lots of blank dvds here. I checked my home partition. I guess, most of my important data are synced with Dropbox. I just need to backup school documents and pictures. Most of my space is occupied by multimedia, stuff that I don't need to backup.

For now, I'll backup with dvds then think thrice or even more if I'll continue resizing partitions.

Btw, my drive is just about 80% full. I just deleted a lot of big bad not-so-important files.

:)

---

### Post by jespdj on 2009-02-28
> **wersdaluv said:**
> It's just that, my /home partition is 113gb big with 107gb used.That's a huge amount of personal data. I don't have an external HD or any other storage to backup it to. My most important files are backed up by Dropbox but that's just 1gb of data. Losing the 112gb would still be very painful.
You MUST make backups, even if you're not going to do anything to your partitions.

Harddisks are typically one of the first things that break in a computer - someday you WILL have a problem with your harddisk and if you do not have a backup then your data will be GONE.

If you care about your data, then buy an external harddisk for backups.

I've seen too many crying people who've lost years of digital photos because they did not make backups... :(

---

### Post by wersdaluv on 2009-02-28
> **jespdj said:**
> You MUST make backups, even if you're not going to do anything to your partitions.

Harddisks are typically one of the first things that break in a computer - someday you WILL have a problem with your harddisk and if you do not have a backup then your data will be GONE.

If you care about your data, then buy an external harddisk for backups.

I've seen too many crying people who've lost years of digital photos because they did not make backups... :(
Aw. Thanks for the advice. After all, these blank DVDs just cost $20 cents. I'm burning a backup of my docs now :D

---

