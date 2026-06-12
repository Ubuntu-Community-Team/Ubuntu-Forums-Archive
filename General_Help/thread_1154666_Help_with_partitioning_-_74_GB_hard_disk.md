---
title: "Help with partitioning - 74 GB hard disk"
date: 2009-05-10
forum: General Help
---

### Post by Ubuntu Terrier on 2009-05-10
Hello,

I'm about to install Ubuntu 9.04 64bit on my pc.
How would you partition a 74 GB hard disk for normal desktop use? Which filesystems would you use?
I've got 4 GB of ram memory and I don't have intention to use hibernation.

Will I be able to clone easily these partitions to another bigger hard disk without any problem (grub?) ? Are there already built-in linux tools to do this ?

My intention is to set up the system first on this smaller hard disk, then get later a single bigger one so that I can clone there my old system and add a /media partition for my multimedia data (videos, mp3s, etc).

---

### Post by x33a on 2009-05-10
give at least 15GB for root partition, you can give the rest to /home, or make storage partitions.

use ext4 for / and /home, and use ext3 for data storage.

and, you should be able to clone your discs. there are a variety of tools available for the same. a good builtin option is dd command.

---

### Post by Ubuntu Terrier on 2009-05-10
Thanks for your reply.

I wasn't very sure of how much space to use for / , but if you say that *at least* 15 GB are needed, I guess more is better, right? How much more, that is the question, though.

---

### Post by -kg- on 2009-05-10
> **x33a said:**
> give at least 15GB for root partition, you can give the rest to /home, or make storage partitions.

use ext4 for / and /home, and use ext3 for data storage.

and, you should be able to clone your discs. there are a variety of tools available for the same. a good builtin option is dd command.

That should be sufficient, but don't forget that you'll need a swap partition.  I would create your / (root) partition at the beginning, create your swap (if you're not going to hibernate, you'll probably be able to get by with a couple of GB, but just to make sure, make it 4 GB or a bit over) at the end of the hard drive, and then use the remaining space for /home.

Of course, it all depends on what you intend (or anticipate) on doing with your computer.  I feel that I have a crap-load of software installed (compilers and other various software), and I have yet to break the 5GB level in my root partition, but 15 GB isn't unreasonable. I've used even less in my /home partition, but I share between that and other ntfs and fat partitions, which mitigates that.  I have a total of around 1.5 TB of hard drive space internally, and then there is my 1 TB external HD, which is shared between my desktop and my laptop.

While the "dd" command is basically "internal" to Linux for copying and backing up partitions, there are external tools that make the process easier, like Clonezilla and the like.  If you would like a more comprehensive look at partitioning and backup, check out [How To Partition]("https://help.ubuntu.com/community/HowtoPartition") from the Community Documentation.

---

### Post by Ubuntu Terrier on 2009-05-10
If it helps to know, my computer will be used to:

- Do some video editing
- Do some audio editing
- Do some large size (high memory) creative works under GIMP with my Wacom graphics tablet
- Use Openoffice mainly to open and process a few rather large spreadsheets I made
- Simple programming/scripting with Java, Python and probably C/C++
- Do basic Internet surfing, mail, irc, audio and video playing
- Probably make some midi/music editing (as I have a digital midi piano/keyboard)

Also, it will be always on mainly for torrent seeding and continuously download a few low-bandwidth streams (long story short)

So, if I understood correctly, of these 74 GB (68.9 GiB):

15 GiB will be for /
50 GiB will be for /home
04 GiB will be for /swap

But maybe a 20/45/4 GiB partitioning could be "safer" ? I don't intend to install too many programs (also I don't play games on my pc), but don't want to risk to run out of space.

---

### Post by -kg- on 2009-05-10
Well, let's put it this way; software is installed in root.  Usually, your files (like video, audio, graphics, spreadsheets, etc., are stored in /home.

Adjust as you think best, considering the approximate size of some of your files as well as your anticipation of the size of software installs.  I still think 15 GB is plenty for your root partition, but whatever you think.

Another consideration for you; if you can get hold of another hard drive or an external hard drive, you can store some files there, as well, which would extend your storage capacity greatly.

---

