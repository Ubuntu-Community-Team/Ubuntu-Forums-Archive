---
title: "Intrepid: Nautilus hangs on large dataset copy on ext HDDs"
date: 2009-02-09
forum: General Help
---

### Post by Donalb on 2009-02-09
Hey all, 
Ok I have a 300, & 2x250gb extrenal USB HDDs.

When doing a copy or move of large amount of data, i.e. say > 30gb from one drive to another, everything starts fine, but after some time, >1 hour, the File Operations dialog box will still be open , it will look fine, (date xfer rate, no. of files, size & time remaining) the source drive may even be thunking away, but it seems stuck/hung on some loop.
This was repeating, using different data sources (movies/audio files) and destinations.
(I also have 2 Iomega external Rev drives, UDF format, 35 & 70gb).

I suspected one HDD of possible disk errors causing some of the issues so did a low level format, no problem, hours long though. When next doing a 140 gb copy to that HDD again it got stuck around 60gb.

This problem has repeated as I say, with large data sets, regardless of source/destination of the various drives.
Data sets of up to around 10 or 15 gb seems ok. There's a grey area above that before I know it's definitely happening from 30gb up.

Apport never launches with an crash. When I close/cancel the task Nautilus will hang, probably requiring a system reset.

Thoughts on where I should go with this?
I don't do a lot of copying data sets this size, but it's a pain when I do.

---

### Post by Donalb on 2009-02-11
Bump. I'm having no luck with my recent problems. It seems if you're a complete noob or an old pro you have a better chance of getting help. These oddball problems I'm having are generating no responses. I'm writing all this in lieu of a "bump".

---

### Post by Donalb on 2009-02-18
Bumpity bump. Can anyone recommend at least a way of trapping the error or finding out what's causing it?

---

### Post by Lambdoid on 2009-04-23
I have this problem as well. It's really annoying as I want to back up my home folder prior to upgrading to Jaunty. Have you reported this as a bug via Launchpad?

---

### Post by ticket on 2009-06-26
I have also experienced this. I used Nautilus to move a large folder to another drive (e.g. ~9Gb containing 80,000 files) by drag-n-drop. The operation proceeded and completed ok, but I noticed Nautilus had by then consumed 190Mb of my 512Mb RAM, and didn't want to release it!  

I ended up re-booting.

With bigger transfers (e.g a full disc copy) I can imagine Nautilus will hang the system, having consumed all memory.

Maybe a command line copy would work better (e.g. rsync).

This bug has been opened and closed a few times now. Nothing ever seems to get done about it.

---

### Post by msully725 on 2009-08-19
I've just seen this happen with a 17 GB transfer. It got to 10.6 GB in a couple minutes, but then hung at 10.6 for 30 minutes. Also, the entire computer began slowing down and I noticed the swap was growing over 1 GB. System has 4 GB of memory and rarely touches swap. 

Not sure, but the heavy swap usage seems like it could be playing a part in transfer hang. Anyone else also see swap usage skyrocket?

---

### Post by narcisgarcia on 2009-12-18
I often have this annoying experience when transfer data through network, both with Ubuntu 8.10 and Ubuntu 9.04

The same effect has to transfer a big file than a large amount of files.

---

### Post by shields on 2010-03-12
I have this happen when I transfer from on folder to the other on my SATA drive. It even happens when I use cp.

Bumpity-Bump-Bump-Bump. :D

---

### Post by Partan on 2010-03-17
I have the same problem when I want to copy a large file (> 2 GB) or a lot of file (> 2 GB) by drag-and-drop via Nautilus. It goes smooth for a while and then just stop with an error message.
I am allready running the most actual version of 10.04.

---

### Post by bossdak on 2010-05-19
I also encounter this problem on my phenom ii setup using lucid 64 but i cannot reproduce the problem on my acer 1810 laptop also running lucid 64.

the problem is not exactly repeatable. if, say i copy the same files to the same directory, sometimes the whole computer locks up, sometimes only the copy progress stops, or my hdd cannot be accessed  anymore.

the problem happens when i copy using cp command in terminal or using nautilus.

previously, the problem occurs at 3GB/350GB files copied. after i disable the 32 bit mode in hdd settings in bios, i can manage to do around 200GB/300GB copy.

the system freezing during intensive disk access was solved by passing elevator=deadline in the kernel.

things to try: disable acpi, try /feisty/gutsy/hardy/intrepid/jaunty

---

### Post by alvarf on 2010-05-21
I have got the same problem. Have done a fresh installation Lucid Lynx 10.04 on a new hard-disk within a IBM T61 laptop. When I copy a lot of files by copy/paste via Nautilus from my QNAP NAS server it goes smooth for a while and then just stop. There is total no network activity and I need to kill the nautilus process to get everything released. Looking throughout the web there are a lot of people with the same issue, so this should be a bug within 10.04.

#UPDATE#

Mounting the NAS share to mount point and then copying the files does work fine.

---

### Post by bossdak on 2010-05-26
my other linux iso was corrupted so i cannot try them. it happens that there is a new bios update for my mobo and it somehow solved the problem. my mobo is j&w minix 785g.

---

### Post by JakcV on 2010-10-27
I have the similar problem at 9.10. There is still a little problem in 10.04 but not so serious. At 9.10, the system can be said unrespond. What i do is renice the nautilus to a hight value, 10 may be, then the system will be able to do other job. I saw front the top, all the cpu resource is at the waiting state for the i/o to complete, therefore the cpu can't do other work. It is my observation, not sure is it correct or not.


p/s: The nautilus will eat up all the cpu resource but the system still respond in 10.04 although is slower.

---

### Post by rldsoftware on 2011-03-20
In Ubuntu 10.10 i also experience this problem, when copying large datasets of large single files (just now with a 2.8GB iso) in Nautilus my complete gnome envirionment hangs requiring a hard reset. This was from an external USB harddisk to (and from) my sata harddisk in my laptop.

Does anyone know if this is a known problem for nautilus, or is it another process that locks up?

---

### Post by widda on 2011-03-26
Ok there's the thousand words, here's the picture (transferring Music folder from 120Gb Vaio USB to Home in Lucid LTS.)
 Now KILObytes/sec is sounding magnificent!

---

### Post by rabinnh on 2011-06-13
I've been having this problem for years (now on Maverick).  It never gets fixed.  I just think of it as strolling down memory lane; you know, Windows Explorer.

---

### Post by Asmodai on 2011-06-13
Are you sure that this isn't a hardware problem?
I know someone who is having similar problems with Windows 7 (entire machine often locking up when accessing internal or external hard disks). So either W7 has a similar bug or it might be somehow hardware-related.

For the record, I have a total of six hard disks (four internal, two external) and I never experienced such a lockup in Ubuntu, even though I frequently copy data around.

---

### Post by rewyllys on 2011-06-13
> **Asmodai said:**
> . . . . For the record, I have a total of six hard disks (four internal, two external) and I never experienced such a lockup in Ubuntu, even though I frequently copy data around.
Likewise, I have never had this problem.  My "immunity" may be related to the facts that I have 8GB of RAM and 20GB of swap file.

---

### Post by widda on 2011-06-13
Since I posted, I just don't use my external HD, even tho it holds heaps of my music and photos. I'm not quite resigned to doing it manually. But I have these 4 suggestions to work on (after translating them!).  So, that is good and welcome!  20GB of swap file.

What i do is renice the nautilus to a hight value,

new bios update for my mobo 

Mounting the NAS share to mount point and then copying the files does work fine.

20GB of swap file.

Thanks , and this:

Are you sure that this isn't a hardware problem?

---

### Post by widda on 2011-06-13
[IMG]file:///tmp/moz-screenshot.png[/IMG]I also get In/Out errors for a minority of music files. Don't see why 3 of 20 tracks *on same album* have permissions variation?

---

### Post by Meneer Jansen on 2011-06-19
Had the same prob. Plugging the power adapter into an other wall socket solved the prob for me. 

However, Nautilus still exits (crases) after moving a file... Very strange indeed.

---

