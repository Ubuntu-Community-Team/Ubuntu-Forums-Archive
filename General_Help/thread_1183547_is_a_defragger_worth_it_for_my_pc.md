---
title: "is a defragger worth it for my pc?"
date: 2009-06-10
forum: General Help
---

### Post by FalloutMan on 2009-06-10
Im a big torrenter, in fact my pc is running 24/7 right now seeding and leeching various files. Since I have crappy DSL I only have 4 active torrents at a time. In a thread where someone posted up a defrag program and a bunch of people said that you dont need a defragger in linux but a few brought up that its good if you are a torrenter since because it is downloading a large file over a period of time, its a lot easier to fragment the files. Maybe its just me, but it feels like my pc is running slower since i started heavy torrenting 3 days ago.  I havent shut down my pc since so I dunno if boot times have increased. I wanna hear your opinions and maybe a suggestion to a program that doesnt run in terminal so I can look at pretty colors.

---

### Post by hansdown on 2009-06-10
Hi FalloutMan.

Ubuntu has the ability to cleanup old files already.No need to install anything.

Just click applications> accessories> terminal.

Enter```
 sudo apt-get autoclean
``` and it will get rid of old files that can slow your machine down over time.

Also make sure your trash is emptied regularly, and you should be fine.

Please note that running four torrents could slow things a little.

---

### Post by jacksaff on 2009-06-10
The file system ubuntu uses (ext3) is fairly resistant to fragmentation. Resistant enough that nobody has ever felt the need to do a gui defragging program for it. It does however start to fragment a lot when the disk gets very near full. If you are over 90% full and using the disk a lot you may get disk related slowdowns.

apt-get clean just gets rid of apt's cache. This can help if your root partition is small as the cache goes there and can fill it up leading to the slowdowns mentioned above.

User files such as bittorrent stuff will be in your home partition which hopefully is large enough to not cause any problem.

---

### Post by regala on 2009-06-10
> **hansdown said:**
> Hi FalloutMan.

Ubuntu has the ability to cleanup old files already.No need to install anything.

Just click applications> accessories> terminal.

Enter```
 sudo apt-get autoclean
``` and it will get rid of old files that can slow your machine down over time.

Also make sure your trash is emptied regularly, and you should be fine.

Please note that running four torrents could slow things a little.

note that apt-get autoclean will hardly remove any file...
quoted from apt-get manpage:
"autoclean
           Like clean, autoclean clears out the local repository of 
           retrieved package files. The difference is that it only
           removes package files that can no longer be downloaded, and
           are largely useless. This allows a cache to be maintained
           over a long period without it growing out of control. The
           configuration option APT::Clean-Installed will prevent
           installed packages from being erased if it is set to off."

so apt-get clean would be better if your goal is really to clean the apt archives (which is a good thing to do as installed packages are not to be installed in the near future)
(for those not understanding, autoclean and clean won't do a thing outside /var/cache/apt/archives)

---

### Post by lovinglinux on 2009-06-10
I don't think a torrent would cause fragmentation, specially if you setup the client to use full allocation. This means it will reserve the space required for the file being downloaded before starting it, so it shouldn't be saved all over the place, but in a contiguous space instead. 

Downloading torrents can slow things a little bit during the download.

> **jacksaff said:**
> The file system ubuntu uses (ext3) is fairly resistant to fragmentation. Resistant enough that nobody has ever felt the need to do a gui defragging program for it. It does however start to fragment a lot when the disk gets very near full. If you are over 90% full and using the disk a lot you may get disk related slowdowns.

To complement the quote above, you have to consider that hard drive reading is faster at the beginning of the disk and slower at the end, due to radius diameter. So if your disk is 90% full, than the probability of saving and reading data from slower parts of the disk are greatly increased, which could affect performance considerably.

---

### Post by sedawk on 2009-06-10
To defrag a file system might improve performance on a single task and
single user computer, but reading (and writing) four or more files (here torrents) more or less in parallel will always result in lots
of head movements on the disk. So defragmentation will not improve
the performance. To check disk I/O you can install the "sysstat" package
and use "iostat". It will show you summaries of the disk usage.

(Some people argue that the time and energy you spend while
 defragging is always wasted time because you never get it back in savings.
 E.g. if you win 10 seconds of startup time after 4 hours of
 defragging you have to start the computer 1440 times to get even.
 For a computer started once a day that takes 4 years. But after
 6 months your file system is fragmented again ...).

---

### Post by l-x-l on 2009-06-10
> **sedawk said:**
> 
(Some people argue that the time and energy you spend while
 defragging is always wasted time because you never get it back in savings.
 E.g. if you win 10 seconds of startup time after 4 hours of
 defragging you have to start the computer 1440 times to get even.
 For a computer started once a day that takes 4 years. But after
 6 months your file system is fragmented again ...).

...Interesting.

---

### Post by TrakerJon on 2009-06-10
All file systems get fragmented...yes, even UNIX and Linux...defragmenting does improve overall performance and not just at startup.

This should help...

Defrag (or fidefrag I should say)

sudo apt-get install bzr python-psyco
bzr branch lp:fidefrag
cd fidefrag/src
sudo python fidefrag.py -d /<directory name>


Don't defrag /sys (you won't like the result) I usually just defrag /usr /home /var /lib and /etc

---

### Post by FalloutMan on 2009-06-10
> **TrakerJon said:**
> All file systems get fragmented...yes, even UNIX and Linux...defragmenting does improve overall performance and not just at startup.

This should help...

Defrag (or fidefrag I should say)

sudo apt-get install bzr python-psyco
bzr branch lp:fidefrag
cd fidefrag/src
sudo python fidefrag.py -d /<directory name>


Don't defrag /sys (you won't like the result) I usually just defrag /usr /home /var /lib and /etc

could I just tell it to defrag everything but put in an --exclude /sys and have it skip it? thatd be easier than doing a defrag a bunch of times.

---

### Post by CatKiller on 2009-06-10
Move your files to another partition and then move them back. Presto, they are no longer fragmented. You can use tar if you're feeling flash. You can even do it as part of your normal backup regime.

---

