---
title: "Copyng of large file lock my system"
date: 2008-12-21
forum: General Help
---

### Post by psychok9 on 2008-12-21
My specs:
Q6600@3.2GHz, P5Q Deluxe with Intel ICH10 southbridge and AHCI mode HDDs, 2x160Gb Seagate SATA, 1x500Gb Samsung SATA.
The copyng of very large file lock Firefox (go grey for a while) and my navigation... How can I fix this problem and improve the copyng performance?
All partitions used on copyng are Ext3.

Thank you in advance.

---

### Post by mdurham on 2008-12-21
Why are you using Firefox to copy files? How do you do that?

---

### Post by dcstar on 2008-12-22
> **psychok9 said:**
> My specs:
Q6600@3.2GHz, P5Q Deluxe with Intel ICH10 southbridge and AHCI mode HDDs, 2x160Gb Seagate SATA, 1x500Gb Samsung SATA.
The copyng of very large file lock Firefox (go grey for a while) and my navigation... How can I fix this problem and improve the copyng performance?
All partitions used on copyng are Ext3.

Thank you in advance.

Depending on what you are using to copy, you could be possible filling up your /tmp directory and probably your root filesystem - which will cripple your system.

---

### Post by flyingbrass on 2008-12-22
I suspect the OP means his whole system is practically unusable when large files are being copied.  The hard drive stays tied up until the copying (or any other disk-intensive task) completes.  I and others suffer the same thing.  The problem hasn't been pinned down yet.  See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094)

I didn't notice improvement when trying different schedulers.

---

### Post by psychok9 on 2008-12-22
> **mdurham said:**
> Why are you using Firefox to copy files? How do you do that?
Sorry for my english. I copy with "normal" nautilus "copy & paste".
> **dcstar said:**
> Depending on what you are using to copy, you could be possible filling up your /tmp directory and probably your root filesystem - which will cripple your system.
I've tried a copy from 1 HDD to another HDD (another partition of another hdd).
> **flyingbrass said:**
> I suspect the OP means his whole system is practically unusable when large files are being copied.  The hard drive stays tied up until the copying (or any other disk-intensive task) completes.  I and others suffer the same thing.  The problem hasn't been pinned down yet.  See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094)

I didn't notice improvement when trying different schedulers.

Yeah... I love Ubuntu and I hope that this bug will be fix soon, it's very annoying.

---

### Post by dcstar on 2008-12-22
> **psychok9 said:**
> Sorry for my english. I copy with "normal" nautilus "copy & paste".

I've tried a copy from 1 HDD to another HDD (another partition of another hdd).


On my 8.04 64-bit system, I am currently copying 16.5GB from one part of my secondary HD to another, and my system response is normal (4.5GB done as I type this, @17.3 MB/Sec). BTW, the partitions in the copy are Reiserfs.

One thing pointed out in the Launchpad entry was that disabling/removing Tracker helps things, I removed this package ages ago as I found it was a useless resource hog.

---

### Post by psychok9 on 2008-12-22
It's "tracker-applet"? (application on start of Ubuntu/Gnome).
I'll try soon a copy without this... thanks!
I use last kernel on proposed repository (.11) and Ubuntu 8.10.

How can I check if DMA and SATA work with ICH10? A program benchmark for hdd & for Linux exist?
Thank you!

---

### Post by dcstar on 2008-12-22
> **psychok9 said:**
> 
........
A program benchmark for hdd & for Linux exist?
Thank you!

```
hdparm -tT /dev/whatever
```

---

### Post by sedawk on 2008-12-22
You can try to run nautilus from command line with lower scheduling
priority:
```

nice nautilus

```

Did this improve the situation when copying files?

(Another test would be to run the copy command ("cp _from_ _to_") from
 command line and measure the performance with "time cp _from_ _to_").
Most likely also "cp" is slowing down as soon as you start something
else.
The concurrent requests to the hdd make everything look slow.

(Have you ever seen the assistent of a piano player turning the
 pages of the music score? Imagine three piano players playing in parallel
 and the assistent has to serve all of them. Piano players will not
 be able to play smooth anymore - and worse, head movements of a
 hdd are really slow, imagine the assistent has to fetch every
 new page from a room in the cellar.)

When I'm risking to slow down (a multi-user) system by copying large
amounts of data I usually use "rsync" instead of "cp" because I can
set the maximum bandwidth used for copying.

---

### Post by psychok9 on 2008-12-25
> **dcstar said:**
> ```
hdparm -tT /dev/whatever
```
Thank you!
> **sedawk said:**
> You can try to run nautilus from command line with lower scheduling
priority:
```

nice nautilus

```

Did this improve the situation when copying files?

(Another test would be to run the copy command ("cp _from_ _to_") from
 command line and measure the performance with "time cp _from_ _to_").
Most likely also "cp" is slowing down as soon as you start something
else.
The concurrent requests to the hdd make everything look slow.

(Have you ever seen the assistent of a piano player turning the
 pages of the music score? Imagine three piano players playing in parallel
 and the assistent has to serve all of them. Piano players will not
 be able to play smooth anymore - and worse, head movements of a
 hdd are really slow, imagine the assistent has to fetch every
 new page from a room in the cellar.)

When I'm risking to slow down (a multi-user) system by copying large
amounts of data I usually use "rsync" instead of "cp" because I can
set the maximum bandwidth used for copying.

Thank you for your great explanation!
This process, on "another operating system", is with low priority (or I think it) and don't break navigation/web surfing.
I will try "nice 15 nautilus" :)
Thank you again!
p.s. sorry for my english, I hope is it understandable :popcorn:

---

### Post by Colt45 on 2008-12-25
> **sedawk said:**
> You can try to run nautilus from command line with lower scheduling
priority:
```

nice nautilus

```

Did this improve the situation when copying files?

(Another test would be to run the copy command ("cp _from_ _to_") from
 command line and measure the performance with "time cp _from_ _to_").
Most likely also "cp" is slowing down as soon as you start something
else.
The concurrent requests to the hdd make everything look slow.

(Have you ever seen the assistent of a piano player turning the
 pages of the music score? Imagine three piano players playing in parallel
 and the assistent has to serve all of them. Piano players will not
 be able to play smooth anymore - and worse, head movements of a
 hdd are really slow, imagine the assistent has to fetch every
 new page from a room in the cellar.)

When I'm risking to slow down (a multi-user) system by copying large
amounts of data I usually use "rsync" instead of "cp" because I can
set the maximum bandwidth used for copying.

While using nice and ionice for individual processes is a partial workaround it does not really address the issue of removing commandline from the entire process.

New users and lazy individuals just want things to work. Commandline can be confusing to some people.  There needs to be a way to configure and tame file copy operations as a whole at the time of boot so that the performance of desktop operations, popular applications, and audio/video playback is not significantly reduced.

---

### Post by birddog165 on 2009-01-26
> **psychok9 said:**
> My specs:
Q6600@3.2GHz, P5Q Deluxe with Intel ICH10 southbridge and AHCI mode HDDs, 2x160Gb Seagate SATA, 1x500Gb Samsung SATA.
The copyng of very large file lock Firefox (go grey for a while) and my navigation... How can I fix this problem and improve the copyng performance?
All partitions used on copyng are Ext3.

Thank you in advance.


Has your hard drive ever unmounted itself?

---

### Post by birddog165 on 2009-01-28
Just a quick question? By any chance do you have any virtualization software (ie. Parallels, VirtualBox, etc) installed?

---

### Post by psychok9 on 2009-02-14
> **birddog165 said:**
> Has your hard drive ever unmounted itself?
I don't think, if I've understood you (I'm not english motherlanguage :P).
> **birddog165 said:**
> Just a quick question? By any chance do you have any virtualization software (ie. Parallels, VirtualBox, etc) installed?

I've Virtualbox installed.
ATM, I've tested on Jaunty: from RAID0 Ext4 partition to Ext3 backup partition... and seem slow only a little firefox process :P
Same Ext3 to Ext4 :P
Soon I want test it with a very large file (> 5Gb) or more files.

---

