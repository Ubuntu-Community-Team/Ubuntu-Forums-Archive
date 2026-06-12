---
title: "Why Linux root partition only needs 10 GB max?"
date: 2009-03-12
forum: General Help
---

### Post by UranUtan on 2009-03-12
Hi,

I have prepared a few VM running Windows Server 2003 and 2008. After applying Service Packs and running Windows Update. The drive C consumes quite a lot of space (about 10 GB for Windows 2003 and 15 GB for Windows 2008). And this amount will increase overtime with all the system updates.

Then I remember the guidelines for manual partitioning in Linux. It is advised to reserve a partition no more than 10 GB for the root. Granted there is some other GB for the swap partition. 

Assuming I have a very roomy partition for /home. I wonder how Linux can spend a lifetime within a 10 GB partition. Where does its find enough room for the temp files or storing all the system updates that I do frequently?

---

### Post by miegiel on 2009-03-12
10GB would be enough for me, I'm only using 5.3GB of the 20GB I made for the root partition. With a separate /home partition you don't need that much.

---

### Post by UranUtan on 2009-03-13
> **miegiel said:**
> 10GB would be enough for me, I'm only using 5.3GB of the 20GB I made for the root partition. With a separate /home partition you don't need that much.

Me too, I allocated 20GB for / and have separate partition for /home. Although guidelines says 10 GB for /, I allocated 20 GB because I have plenty of room in the hard drive (and a little bit paranoia from Windows reflex). However, I am really puzzled as how Linux system can live forever with such few storage space, especially when I run auto updates frequently.

---

### Post by heindsight on 2009-03-13
Well, temporary files are just that, temporary - they get deleted every once in a while to save space.

/usr requires a few gigabytes of space for installing applications (my /usr is on a separate 6.7GB partition and currently uses about 3.6GB). It will of course grow over time as you install more applications.

/var may require some space, depending on what you use the machine for. For example, database software often stores databases there, and various other applications keep persistent data there so it may require some space and grow over time.

/srv might need some space and grow over time if you're hosting web services or FTP services, otherwise chances are your /srv will never take up much space.

Some third party software sometimes installs into /opt. If you're installing anything like that you may need some space there, otherwise it will hardly take up any space.

/etc may grow a bit over time since it contains configuration files for just about everything you install, but those files don't take up that much space so it will never get too big.

With the obvious exception of /home, the rest of the toplevel directories in / hardly need much space (some like /dev /proc and /sys don't take up any disk space) and are unlikely to grow much with time.

In fact, since I don't use any software that needs lots of space under /var, no web servers or ftp servers that use /srv and no 3d party software that installs to /opt, I have /opt /srv and /var all on my / partition: a 2.8GB partition of which only 1.1GB is in use.

So depending on how you use your machine and what you install you can even get away with as little as 5GB for your / partition (and that's including /usr).

---

### Post by UranUtan on 2009-03-13
Thank you very much for taking the time to give a detailed answer. Just for my learning experience. Let say one day my root partition runs out of space. What would be the proper treatment?

1. Identify which top folder need space. Let's say, it is the /usr that eats all the space. Is it possible to move this /usr folder to a bigger partition?

2. Or simply use Gparted and try to resize the root partition?

Thanks in avance.

---

### Post by heindsight on 2009-03-13
> **UranUtan said:**
> Thank you very much for taking the time to give a detailed answer. Just for my learning experience. Let say one day my root partition runs out of space. What would be the proper treatment?

1. Identify which top folder need space. Let's say, it is the /usr that eats all the space. Is it possible to move this /usr folder to a bigger partition?

2. Or simply use Gparted and try to resize the root partition?

Thanks in avance.

There would be many options.

The simplest would be if you had another partition with plenty of unused space, in which case you could just shrink that and grow your / partition.

Alternatively, you could spend some money on a second hard drive, in which case you'd have numerous options for moving things from your / partition to new partitions on the new hard drive or moving existing partitions from your old hard drive to the new one and growing your / partition etc. 

All of this involves quite a lot of work though, and deciding just how much space to allocate for each partition can be quite challenging. When I first started using GNU/Linux I often used to do several reinstalls, changing the partition sizes each time, before I got to a point where I could be satisfied with my partitioning scheme.

This is one of the reasons LVM was invented. [http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/). It makes the task of growing and shrinking partitions, moving partitions from one disk to another much simpler and even allows you to have volumes spanning more than one disk. Unfortunately, LVM is not available in the default Ubuntu installation you have to use the alternate install CD to be able to use LVM.

---

### Post by lykwydchykyn on 2009-03-13
I used to say 10 Gb, but it's certainly easy to use that up if you're loading up a lot of big programs like 3D games, multiple DE's and so forth.  If you have oodles of space, no need to cut things tight.

---

### Post by heindsight on 2009-03-13
> **lykwydchykyn said:**
> I used to say 10 Gb, but it's certainly easy to use that up if you're loading up a lot of big programs like 3D games, multiple DE's and so forth.  If you have oodles of space, no need to cut things tight.

True enough. 

Personally, I prefer to keep my / partition small (no more than 3GB) and then have separate, bigger partitions for things like /var (if i'm going to need lots of space there), /usr and /home.

---

### Post by Slim Odds on 2009-03-13
> **heindsight said:**
> Personally, I prefer to keep my / partition small (no more than 3GB) and then have separate, bigger partitions for things like /var (if i'm going to need lots of space there), /usr and /home.

I mostly agree....

You really have to understand how the file system works and where it puts stuff.

For example: there might be times when you need a lot of space in /tmp. Like if you're coping a DL data DVD, the copy program might want to read the entire DVD first, then write it.
In that case you might want to have at least 8.5G available for /tmp

I typically use separate paritions for / /var /tmp /usr /boot and /home (even on non-server desktop computers).

/var can be known to use up all of your space if a service that uses logging gets out of control.

---

### Post by Neo_The_User on 2009-03-13
I have everything on 1 partition (plus swap on sda5) and I was wondering, is this considered BAD? It's an 80GB hard drive with a 78.1 GB root partition.

---

### Post by Slim Odds on 2009-03-13
> **Neo_The_User said:**
> I have everything on 1 partition (plus swap on sda5) and I was wondering, is this considered BAD? It's an 80GB hard drive with a 78.1 GB root partition.

I'm most cases, it's just fine..

---

### Post by mb_webguy on 2009-03-13
> **Neo_The_User said:**
> I have everything on 1 partition (plus swap on sda5) and I was wondering, is this considered BAD? It's an 80GB hard drive with a 78.1 GB root partition.

Yeah, that's fine.  That's the default partitioning scheme and the simplest one, and the one used by Dell on their Ubuntu-installed computers from what I've seen.

Linux is very flexible about partitions, since a partition can be mounted anywhere in the filesystem.  I personally like to have a small root partition -- I'm using a little less than half of a 12GB root partition, which *lots* of software installed -- and a separate home partition, since I like the idea of keeping the OS and user data separate.  For a dual-boot setup with Windows, I'll have a small partition for each OS, a very small (<2GB) home partition for Linux, and a shared data partition using the rest of the drive space.

But there are countless ways of partitioning your computer, and which is best depends on your personal preference and how you use your computer.  As long as your partitions are large enough to contain whatever you have them mounted as, there isn't a "wrong" partitioning scheme.

---

### Post by CREEPING DEATH on 2009-03-14
> **Neo_The_User said:**
> I have everything on 1 partition (plus swap on sda5) and I was wondering, is this considered BAD? It's an 80GB hard drive with a 78.1 GB root partition.

My first setup was that way, no issues, BUT having a separate /home keeps your data safe if you hose the OS.

CD

---

### Post by dcstar on 2009-03-14
> **mb_webguy said:**
> 
.........
But there are countless ways of partitioning your computer, and which is best depends on your personal preference and how you use your computer.  As long as your partitions are large enough to contain whatever you have them mounted as, there isn't a "wrong" partitioning scheme.

Keeping all data in a single partition increases the risk of data loss when power failures or system problems occur.

Any problem when the system is writing to the single area of directory information can cause anything from minor corruption through to total system loss - and if you have everything continually writing to a single area then the odds of corrupting that are greatly increased.

Having different partitions for important data is a proven way of reducing risk of data loss in this scenario, as well as others like reducing the risk of a full data folder crashing the O/S.

If there is any "wrong" partitioning scheme, it is having everything in a single partition.

---

### Post by nelskurian on 2009-03-14
> Why Linux root partition only needs 10 GB [COLOR="Red"]max[/COLOR]?..I dont think 10GB maximum...

---

### Post by hyper_ch on 2009-03-14
you might want to add more as /tmp can be important when your rip dvds or blurays... of course you could also mount anther partition as /tmp or in the according ripping programs set a different /tmp folder.

---

### Post by UranUtan on 2009-03-14
> **Slim Odds said:**
> You really have to understand how the file system works and where it puts stuff.

For example: there might be times when you need a lot of space in /tmp. Like if you're coping a DL data DVD, the copy program might want to read the entire DVD first, then write it.
In that case you might want to have at least 8.5G available for /tmp

I typically use separate paritions for / /var /tmp /usr /boot and /home (even on non-server desktop computers).

/var can be known to use up all of your space if a service that uses logging gets out of control.

That is the problem, how are these /xxx folders used? Can you give a typical guidelines on how to separate these folders? (for example /dev name and size of what you would do for a typical desktop system?

Let's assume, I don't have the necessary skills to do manual partitioning. I relied on Ubuntu installer to do guided partitioning on the entire disk. Is there any disadvantage in this option?

---

### Post by mb_webguy on 2009-03-14
> **UranUtan said:**
> That is the problem, how are these /xxx folders used? Can you give a typical guidelines on how to separate these folders? (for example /dev name and size of what you would do for a typical desktop system?

Here's a brief explanation of the [Linux filesystem]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").

---

