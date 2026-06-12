---
title: "Want to partition my 500g media hdd to back up itself &amp; my OS hdd - how?"
date: 2008-12-17
forum: General Help
---

### Post by PsychedelicWonders on 2008-12-17
Ok, I have a 40g hdd that has both my Ubuntu and XP PRO OS on a dual boot.

I also have a 500g media hdd where all of my songs, pictures etc are backed up on.

Now I have customized my OS so much, I would hate to lose all of the hours of work I've put into it.

Now once money permits, I will a separate, new 40g hdd to back up the original OS hdd onto and I will also then buy an addtional 500g hdd to back up all of my media on.

But for the time being, I only have the one 500g media HDD and want to maximize it to its fullest, and also safe haven all of my data as possible.

So can I "back up" my entire 40g OS hdd onto my 500g in its own parition in case my 40g crashes?

I also want to back up all of the media on my current 500g hdd in its own partition in case the first partition crashes or gets corrupted.

What I would like to do is partition the 500g in 3 parts:

Part 1: Normal media storage
Part 2: Back up of media storage
Part 3: Back up of OS HDD

Can I do this?

Is it pointless to "backup" my media twice on the same HDD, since if the 500g hdd crashes I'm screwed any ways?

But it would come in benefit in case I deleted all of my music in my main music folder like I just did the other day...

How would I go about this?

How would I set up the hdd's to automatically back themselves up at a particualr time so I dont have to manually do it ever?

---

### Post by Wayne_V on 2008-12-17
For what I read, you may be better off using mondo ([http://www.mondorescue.org](http://www.mondorescue.org)) for the 40G and just a backup directory (not a separate partition) on the 500G for your media backups.   You could just do plain copies to the backup directory or, better yet, set up a subversion repository there ...

---

### Post by PsychedelicWonders on 2008-12-19
> **Wayne_V said:**
> For what I read, you may be better off using mondo ([http://www.mondorescue.org](http://www.mondorescue.org)) for the 40G and just a backup directory (not a separate partition) on the 500G for your media backups.   You could just do plain copies to the backup directory or, better yet, set up a subversion repository there ...

What is that mondorescue exactly?

I tried taking a look at it, but just seems overwelming with all of that code.

What is a backup directory vs. a separate parition to truly RAID all of my files?

And what is a subversion repository?

All of these ideas are new to me, can you explain the pros and cons to them please?

thanks.

---

### Post by hyper_ch on 2008-12-19
"how" do you want to have it backed up? as image?

---

### Post by PsychedelicWonders on 2008-12-19
Umm... not sure really.

I just planned on backing it up with normal files?

I want a complete RAID style back up of all of my files.

What would saving it as an image do?

I have like 470g worth of free space... so I do not need to conserve space really.

Just want to make sure all my media is safely backed up and basically have easy to access duplicates in case my original gets corrupted or deleted.

---

### Post by Therion on 2008-12-19
Simple solution: Use QuickStart.

[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

---

### Post by PsychedelicWonders on 2008-12-19
What is quickstart?

I was honestly just looking for something easy to use like RAID.

I really just want to mirror all of my files.

Can you explain the benefits of this quickstart over RAID?

---

### Post by hyper_ch on 2008-12-19
with a raid you'd need either to get a hardware raid or resetup the system with a software raid.

---

### Post by jerome1232 on 2008-12-19
> **PsychedelicWonders said:**
> 
What would saving it as an image do?


Saving the hdd as an image makes an exact copy of your hdd in one file on the backup media. (if you image the entire  drive it'll contain the boot record and everything) To restore you just write the image back to your original drive. 

You can actually mount the image file as if it were a real drive.

---

### Post by PsychedelicWonders on 2008-12-22
I would prefer a method that has an auto-clock to back up the files I specify like every 24 hours so it always has the most up to date backup of my main files... is this more along the lines of RAID?

---

### Post by PsychedelicWonders on 2008-12-23
Bump

---

### Post by fjgaude on 2008-12-23
With some types of raid you have full backup, redundancy, i.e., raid1 and raid5.

You might study up on raid with these and more:

[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)

Try reading the **man** pages for **mdadm** after you install it.

```
sudo apt-get install mdadm
```

Let us know how you are doing.

---

