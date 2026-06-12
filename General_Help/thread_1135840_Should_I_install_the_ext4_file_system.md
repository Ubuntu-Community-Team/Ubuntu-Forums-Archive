---
title: "Should I install the ext4 file system?"
date: 2009-04-24
forum: General Help
---

### Post by peyre on 2009-04-24
I'm all set to upgrade to 9.04 this weekend (I'll probably do a clean install rather than an in-place upgrade), and I was wondering about the new ext4 fs.  How are things looking?  Is it as reliable as ext3, or would people recommend sticking with the older file system?

---

### Post by cdwillis on 2009-04-24
I know it's not a true benchmark, but overall everything seems faster. I've had no problems. Just go for it.

---

### Post by leonardo_neo on 2009-04-24
> **peyre said:**
> I'm all set to upgrade to 9.04 this weekend (I'll probably do a clean install rather than an in-place upgrade), and I was wondering about the new ext4 fs.  How are things looking?  Is it as reliable as ext3, or would people recommend sticking with the older file system?

I am using ext4, and I have not experienced any of the "known issues" of ext4.

Yes, but there are some issues for sure with ext4 as I read from various forum posts, and independent articles. One of the issue is data loss, or data is not saved.

[http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892](http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892)

I don't know if this issue is fixed by now or not, but it is better if you are alert.

So if you wish to use your computer for storing important documents/data, then you can be more cautious. Even if you wish to use ext4 now, then it is prudent that you have backup of your important documents somewhere else.

---

### Post by sgtbug on 2009-04-24
here is what i did.. kept my /home as ext3 and kept my / as ext4.. so even if ext4 goes crazy, at least my /home is safe..

ext4 is extremely fast.. highly recommended..

---

### Post by paradigm2 on 2009-04-24
> **peyre said:**
> I'm all set to upgrade to 9.04 this weekend (I'll probably do a clean install rather than an in-place upgrade), and I was wondering about the new ext4 fs.  How are things looking?  Is it as reliable as ext3, or would people recommend sticking with the older file system?

There's no question that once ext4 is stable it will be far superior to ext3, but....

It's risky. If you do make sure you have backups of everything that you need.

While many issues seem fixed I still see people with what appears to be ext4 related issues.

---

### Post by Therion on 2009-04-24
> **cdwillis said:**
> I know it's not a true benchmark, but overall everything seems faster. I've had no problems. Just go for it.
Could have been my post.  You'll have to specifically change the setting though, from ext3 (the default) to ext4, during the partitioning stage to get it.

---

### Post by cdwillis on 2009-04-24
> **Therion said:**
> Could have been my post.  You'll have to specifically change the setting though, from ext3 (the default) to ext4, during the partitioning stage to get it.

I wanted to add that I've been using Jaunty since alpha 6 and never experienced any problems, but it's always a good idea to backup crucial documents just in case.

---

### Post by peyre on 2009-04-24
Faster is a wonderful thing, especially on this old beast of a system I'm currently using (vintage 2001).

Backing up my system is of course a must.  I use an external hard drive and try to back up fairly regularly--so that's at least partly covered.

Yes, I'd heard about that solution: using ext4 except leaving /home at ext3.  Anyone else tried that yet?

...Which brings me to my next question, the Howto.  If I read it right, the default install for 9.04 continues to use ext3.  If I go in and set the partitions manually during install, what partitions should I set up exactly?  (I'm awfully shaky on the details of setting up Linux partitions.)  I have a big hard drive (>300GB) and 768MB of RAM.

Sorry for the beginner question.  I know my way around Windows quite well, but I'm still getting started with Linux.

EDIT:  Ok, if I'm reading this right, by default, Ubuntu installs (on my system) sda1 for data as ext3, and sda5 as swap.  So if I wanted to do the same but switch to ext4, I'd just change sda1 to ext4 and give it Mount point /.  If I wanted to do the /home=ext3 thing, I'd do that but also create a partition (sda2 or whatever) as ext3 with Mount point /home.  Is that about right?

---

### Post by dcstar on 2009-04-24
> **paradigm2 said:**
> There's no question that once ext4 is stable it will be far superior to ext3, but....

**It's risky.** If you do make sure you have backups of everything that you need.

While many issues seem fixed I still see people with what appears to be ext4 related issues.

Just read the 9.04 release notes about the EXT4 resize bug.....   :-(

---

### Post by adamlau on 2009-04-24
If you are a bleeding edge user, go for it. I am not, so I stick with ext2/ext3 and XFS for my needs.

---

