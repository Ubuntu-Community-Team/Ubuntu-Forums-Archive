---
title: "How do I defrag my Fat32 without a Windows OS?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by randell6564 on 2006-08-06
Hey all!

I dumped my Windoze a while back, so now I only use ubuntu.

I have a 20gig fat32 drive that I use to store my music and video on. It just occured to me that I will need to defrag this drive occasionally.  How would I go about doing this since I am not using Windoze any longer?

Thanks!

Oh., and Flame away if you want.  I can take it! :)

---

### Post by ardchoille on 2006-08-06
> **randell6564 said:**
> Hey all!

I dumped my Windoze a while back, so now I only use ubuntu.

I have a 20gig fat32 drive that I use to store my music and video on. It just occured to me that I will need to defrag this drive occasionally.  How would I go about doing this since I am not using Windoze any longer?

Thanks!

Oh., and Flame away if you want.  I can take it! :)

The Windows OS is the one responsible for spewing files all over the hard drive and causing it to become fragmented. If you only use Linux, then the drive isn't going to become fragmented to a point worth worrying about, regardless of which file system type it is.

---

### Post by randell6564 on 2006-08-06
> **ardchoille said:**
> The Windows OS is the one responsible for spewing files all over the hard drive and causing it to become fragmented. If you only use Linux, then the drive isn't going to become fragmented to a point worth worrying about, regardless of which file system type it is.

HAAAA! That makes sense!  Now that there is no windoze to fragment it, I dont worry about it!

Thanks a lot, My Friend!

---

### Post by dennisharrison on 2006-08-06
I am actually very interested in re ordering information on different kinds of file systems in linux as I plan on using a live cd to repair a lot of different problems and it would be nice to add defrag to the tool belt also. Any suggestions?

---

### Post by randell6564 on 2006-08-06
> **dennisharrison said:**
> I am actually very interested in re ordering information on different kinds of file systems in linux as I plan on using a live cd to repair a lot of different problems and it would be nice to add defrag to the tool belt also. Any suggestions?

What kind of problems are you having?  As far as I know any kind of dfragging in linux is done at the terminal.

---

### Post by dennisharrison on 2006-08-06
I am not having any problems related to this.  I would just like a live cd to use to repair family and friends computers. Most of them use windows xp.

---

### Post by randell6564 on 2006-08-06
> **dennisharrison said:**
> I am not having any problems related to this.  I would just like a live cd to use to repair family and friends computers. Most of them use windows xp.

Well., I'm somewhat familiar with Windows. (Dont be fooled with the report that windows has done away with DOS!)

As far as a "live cd" that is windows related, I'm clueless accept that any live cd that I have used to install linux can tweak windows partitions, but I'm not sure that they can actually "repair" them. 

The only thing that comes to mind is QTparted or the actual disk manager that is in windows.

---

### Post by dennisharrison on 2006-08-06
thanks I am trolling around looking for something to use now :)

---

### Post by peabody on 2006-08-06
> **ardchoille said:**
> The Windows OS is the one responsible for spewing files all over the hard drive and causing it to become fragmented. If you only use Linux, then the drive isn't going to become fragmented to a point worth worrying about, regardless of which file system type it is.

Actually, that is not true.  Linux based file systems such as ext2 and ext3 resist fragmentation fairly well (although they still fragment, fragmentation is impossible to avoid on *any* file system).  Fat32 on the other hand, fragments like crazy under any OS.  It's a terrible file system (a shame really since it's become the "standard" file system for removable media) because it just continually appends to the free space until there isn't room at which point it finally tries to figure out where it can fit things.

NTFS still fragments although not as bad as the FAT family.  NTFS fragmentation begins to get bad as the disk fills (same with most filesystems, but NTFS doesn't fair as well as others).  Most of NTFS's fragmentation problems come from the fact that most Windows systems do everything on one partition, including swap and data, while Linux systems typically seperate swap from data and seperate data even further into seperate partitions; /usr and / for the system software, /home and /var for constantly changing data.  This keeps fragmentation low on filesystems where the software's kept and lets fragmentation develop where it typically isn't as much of a problem (/home for user data and /var for logs, websites, and databases).

However, that said, defragmenting is merely an optimization.  In other words, if it ain't broke, don't fix it.  If disk access times are making you wait for things to load then fragmentation is a problem.  If you aren't noticing disk latency, then it isn't a problem, no matter what the percentage of file fragmentation is.

According to e2fsck my /home is over 12% fragmented, but I don't notice any speed problems.

---

### Post by randell6564 on 2006-08-07
> **peabody said:**
> Actually, that is not true.  Linux based file systems such as ext2 and ext3 resist fragmentation fairly well (although they still fragment, fragmentation is impossible to avoid on *any* file system).  Fat32 on the other hand, fragments like crazy under any OS.  It's a terrible file system (a shame really since it's become the "standard" file system for removable media) because it just continually appends to the free space until there isn't room at which point it finally tries to figure out where it can fit things.

NTFS still fragments although not as bad as the FAT family.  NTFS fragmentation begins to get bad as the disk fills (same with most filesystems, but NTFS doesn't fair as well as others).  Most of NTFS's fragmentation problems come from the fact that most Windows systems do everything on one partition, including swap and data, while Linux systems typically seperate swap from data and seperate data even further into seperate partitions; /usr and / for the system software, /home and /var for constantly changing data.  This keeps fragmentation low on filesystems where the software's kept and lets fragmentation develop where it typically isn't as much of a problem (/home for user data and /var for logs, websites, and databases).

However, that said, defragmenting is merely an optimization.  In other words, if it ain't broke, don't fix it.  If disk access times are making you wait for things to load then fragmentation is a problem.  If you aren't noticing disk latency, then it isn't a problem, no matter what the percentage of file fragmentation is.

According to e2fsck my /home is over 12% fragmented, but I don't notice any speed problems.

NICE! Good Job! But, just in case I DO want to Defrag my Fat32, How would I go about doing that from ubuntu?

---

### Post by peabody on 2006-08-07
> **randell6564 said:**
> NICE! Good Job! But, just in case I DO want to Defrag my Fat32, How would I go about doing that from ubuntu?

Unfortunately I am unaware of any free software alternative for defragmenting fat32 other than backing up everything on the drive, reformatting it and dumping the backup onto it.  That'll defragment it perfectly of course, as this method works for pretty much any file system.

There may be commercial alternatives that I'm unaware of.

---

### Post by randell6564 on 2006-08-07
> **peabody said:**
> Unfortunately I am unaware of any free software alternative for defragmenting fat32 other than backing up everything on the drive, reformatting it and dumping the backup onto it.  That'll defragment it perfectly of course, as this method works for pretty much any file system.

There may be commercial alternatives that I'm unaware of.

Yeah., THATS no problem for me. Got plenty of room on my Linux partition.

Thanks, My Friend!  You are very concise, yet clear. You should be a teacher, lol!

I noticed that you are fairly new to the ubuntu forum.  Please stick around! You have said a lot in a very short time!

Cheers!

---

