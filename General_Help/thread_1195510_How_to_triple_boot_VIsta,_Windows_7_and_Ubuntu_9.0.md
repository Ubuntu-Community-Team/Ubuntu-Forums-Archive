---
title: "How to triple boot VIsta, Windows 7 and Ubuntu 9.04?"
date: 2009-06-23
forum: General Help
---

### Post by rustynathan on 2009-06-23
I have a dell dual booting Vista and Windows 7 (64 bit). How can I triple boot and add Ubuntu in it? I already have Ubuntu installed on my PS3 and have for a year, so I have experience with Ubuntu.

---

### Post by synapsys on 2009-06-23
All you really need is a hard drive partition in which to place Ubuntu. If Vista and 7 are hogging up the entire hard drive, then this could get tricky. If you have an empty partition of some size, then just install Ubuntu with grub on the mbr.

---

### Post by rushikesh988 on 2009-06-23
Just install ubuntu on the other drive it will automatically dect the Windows 7 Loader.

I have installed triple boots before with XP ,VISTA, UBuntu  and its order of instaliing is XP, VISTA , UBUNTU    (older windows first then New one after that our UBUNTU) 



hope this will help you

---

### Post by rustynathan on 2009-06-23
I have 20 Gbs for Windows 7, about 460 Gbs for vista. It wont let me shrink the Vista partition again in the Vista partition manager even though there is still about 120Gb free.

---

### Post by synapsys on 2009-06-23
be very careful when shrinking partitions! could cause data loss!

That being said, your best bet would be to defrag your vista partition (always defrag before you shrink to minimize data loss) Then fire up a livecd and shrink using gparted. 

!!!IMPORTANT!!! Always backup data on a partition before you shrink it. You always run the risk of losing it completely. Also if you boot from this partition, you may have problems booting also. 

Backup

Backup

Backup

If you are using a desktop computer just buy an additional hard drive and save yourself the trouble.

---

### Post by philcamlin on 2009-06-23
partition trhe hdd in 3 and install the 3 

voila:popcorn::popcorn::popcorn:

---

### Post by rustynathan on 2009-06-23
> **synapsys said:**
> be very careful when shrinking partitions! could cause data loss!

That being said, your best bet would be to defrag your vista partition (always defrag before you shrink to minimize data loss) Then fire up a livecd and shrink using gparted. 

!!!IMPORTANT!!! Always backup data on a partition before you shrink it. You always run the risk of losing it completely. Also if you boot from this partition, you may have problems booting also. 

Backup

Backup

Backup

If you are using a desktop computer just buy an additional hard drive and save yourself the trouble.

I tried to shrink with gparted, but I did not see how. How do I shrink in gparted? Also I have 2 extra 160Gb IDE hard drives, but I did not see any ware to put them in my computer. I would buy a new hard drive, however, I am using my money to get a coumputer for myself so I wont have to use my PS3 anymmore if I am in my room. And so I don't have to worry about crashing the family coumputer with my little "projects" hehe.

---

### Post by synapsys on 2009-06-23
1. Boot up live ubuntu cd

2. Start gparted

3. Right click vista partition
    Click unmount

4. Right click vista partition
    Click resize/move

5. Drag slider to desired size

6. Save changes

---

### Post by rustynathan on 2009-06-23
> **synapsys said:**
> 1. Boot up live ubuntu cd

2. Start gparted

3. Right click vista partition
    Click unmount

4. Right click vista partition
    Click resize/move

5. Drag slider to desired size

6. Save changes

I'll go try that now, I'll post how it goes.

---

### Post by rustynathan on 2009-06-23
Well I did what you said, and it only gives me 2Gb for a new partition.

[[IMG]http://img193.imageshack.us/img193/9703/screenshotegz.th.png[/IMG]]("http://img193.imageshack.us/i/screenshotegz.png/")

---

### Post by synapsys on 2009-06-23
Did you drag that black arrow on the right to the left to shrink it?

---

### Post by rushikesh988 on 2009-06-23
brother u can resize or shrink partitions from vista also for that just right click on manage start -> computer  computer management console will open

then go to drive option that is on left hand side .. and from that u can manage shrink / delete / create new patition

---

### Post by rustynathan on 2009-06-23
When I drag it all the way to the left, it only gives my 904Mb.

---

### Post by synapsys on 2009-06-23
> **rustynathan said:**
> I have 20 Gbs for Windows 7, about 460 Gbs for vista. It wont let me shrink the Vista partition again in the Vista partition manager even though there is still about 120Gb free.

brother

@rustynathan: What do you mean it 'gives' you 904 mb?

---

### Post by rustynathan on 2009-06-23
> **rushikesh988 said:**
> brother u can resize or shrink partitions from vista also for that just right click on manage start -> computer  computer management console will open

then go to drive option that is on left hand side .. and from that u can manage shrink / delete / create new patition
I know. that's how I am dual booting Vista and Windows 7. It does not let me shrink the Vista partition any more though.

---

### Post by rustynathan on 2009-06-23
> **synapsys said:**
> brother

@rustynathan: What do you mean it 'gives' you 904 mb?
Well now it strangely gives me 2048Mb. This is what I mean.
[[IMG]http://img25.imageshack.us/img25/3951/screenshotpzc.th.png[/IMG]]("http://img25.imageshack.us/i/screenshotpzc.png/")

Edit: And wow, even the live cd for PC is 100x faster than on the PS3. I am amazed lol.

---

### Post by synapsys on 2009-06-24
Did you defragment vista before you tried this? Maybe gparted is saving you from deleting files..... 'free space' is not always at the end of the partition when using windows.

---

### Post by rustynathan on 2009-06-24
> **synapsys said:**
> Did you defragment vista before you tried this? Maybe gparted is saving you from deleting files..... 'free space' is not always at the end of the partition when using windows.
 I did not when that pic was taken. I did later though and vista still won't let me shrink, and I have yet to try gparted again. Right now I am tring the "INstall inside windows" option and I'll see how it goes.

---

### Post by rustynathan on 2009-06-24
Alright, well that did it. I'm on Ubuntu right now, thanks guys.

---

