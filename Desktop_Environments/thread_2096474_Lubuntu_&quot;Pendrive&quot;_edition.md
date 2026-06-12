---
title: "Lubuntu &quot;Pendrive&quot; edition"
date: 2012-12-20
forum: Desktop Environments
---

### Post by rvndmnmt on 2012-12-20
Personal project I am working on.  Got bit by the USB bug when I was messing with Puppy but definitely don't like messing with slackware.  They have a Debian compatible version but it is a bit problematic.  

So, to start, I did a lubuntu-core x32 install off of the 12.04 minimal disk.  I'm working with a limited amount of space, I need the greatest cross platform compatibility I can get, and I don't like to repeat myself.  Lubuntu was chosen for it's light weigh.  LTS builds have some downsides as you're not getting bleeding edge features and technology, but there are also some obvious advantages such as 3 years of support and stability.  I really shouldn't care for something that may or may not burn out in 6 months but that is just the beginning of this.

I wanted it to run well, but if possible I would like to use it longer than six months.  I did a little brain storming and decided to treat this thing for what it was closest to.  I cracked my knuckles and went to work.  

USB's have something like 100,000 read/writes, so like an earlier SSD I am going to do what I can to make sure that it doesn't write any more than it has to.  I cracked open the CLI and added a few entries to the /etc/fstab file.  I disabled file access time stamping with noatime and enabled trim with a discard command.  I set up /tmp /spool /and log files on a ram drive as well as the browser cache.  Most of the machines I am going to be using this on have at least 2-3 gig of ram so this shouldn't be to terribly much of an inconvenience. 

I know USB's don't have trim, they do have a crude form of wear leveling but just not that.  Well that I know of.  I don't think it's cost effective but one day, who knows? Besides, if it's not used it's simply ignored.  No harm, no foul.

I set the scheduler for deadline, used for an SSD without TRIM, and called it a day after a few other tweaks to the system here and there.  A curious thing happened though, I experienced random freezes.  No good reason, I would be tooling along and, by my best guess, I didn't say "swiper no swiping" or something to that effect.  Did a little homework and, of course, the USB drive isn't compatible with LinuxNCQ or something to that effect.  So I disabled NCQ in GRUB and haven't experienced any further problems.  On a side note I created a liveCD and loaded it on another 8 gig USB drive and enabled NCQ and haven't run into any problems so this might be drive specific.  I really don't know.

I have it working, mostly.  Still have to map in certain commands i.e. ctrl-alt-del pulling up gnome-system-monitor instead of lxtask and a few other things but this is what I have.

[http://www.youtube.com/watch?v=5oA5Gf75bE4](http://www.youtube.com/watch?v=5oA5Gf75bE4)

I spent so much time on, hopefully, extending the USB drive life.  I just need a fresh pair of eyes to take a look at it and give me some recommendations on what else I can do to clean it up.  I'm not trying to create something for public consumption.  With great power comes great responsibility and all.  I'm just trying to make something that is going to serve me well.  I don't feel like doing the job halfway, I'm just burned out on it right now. 

I could also use some help somehow cloning it into a distributional format and uploading it.  Never really done that before.

---

### Post by sudodus on 2012-12-20
It looks interesting :-)

If you make an image with dd|gzip or even better with Clonezilla: How big would it be? If less than 5 GB, there are serveral free web services, that you could use, for example Google Docs. Remember to add a checksum file too, for example md5sum.txt so that people can check that the downloading was successful. If less than 2 GB there are even more free web services ...

A more advanced way might be to use Remastersys. Browse the internet and read about it, and you might very well choose this way to go.

---

### Post by rvndmnmt on 2012-12-20
> **sudodus said:**
> It looks interesting :-)

If you make an image with dd|gzip or even better with Clonezilla: How big would it be? If less than 5 GB, there are serveral free web services, that you could use, for example Google Docs. Remember to add a checksum file too, for example md5sum.txt so that people can check that the downloading was successful. If less than 2 GB there are even more free web services ...

A more advanced way might be to use Remastersys. Browse the internet and read about it, and you might very well choose this way to go.

I have a copy made with Remastersys, the problem was that some of the settings didn't transfer.  But the copy was reasonably small at 1.1gig.  

I'll check out Clonezilla, was reading a bit on it while I was researching Remastersys.  Thank you for the help :)

---

### Post by sudodus on 2012-12-20
Good luck and keep us informed about your progress, for example when there is an image to download and test :-)

---

### Post by rvndmnmt on 2012-12-24
Alright, here it is.  Been trying to clone this thing successfully but still can't get the /etc/fstab to cross over.  This is what it should look like.  Looks like you are going to have to manually enter this.  Sorry, I tried.


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4e8bd4e5-a6cd-4958-b38b-1d5c8754edf6 /               ext4 errors=remount-ro,noatime,nodiratime,discard 0       1


# /tmp on Ramdrive
tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0
tmpfs /var/spool tmpfs defaults,noatime,mode=1777 0 0
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0


Otherwise, i'll give you a brief list of some of the unlisted software I have installed on this thing so you know what you have to work with.

Joe
Powertop
cpufreqd

A bunch of other stuff I can remember if I take the time to do so.  I was pretty drunk when I came up with the idea let alone implemented it so some things are a bit hazy.  

This is where you can download it, I hope. Looks like you are either going to have to create a google account or sign in to download it.

[https://docs.google.com/folder/d/0B3AekNyPPXEGR0xWTURCZkRRZjQ/edit](https://docs.google.com/folder/d/0B3AekNyPPXEGR0xWTURCZkRRZjQ/edit)

Near as I can tell all you need to do is burn it to disk.  I didn't test the unetbootin route but the live system was created by remastersys.

---

### Post by sudodus on 2012-12-24
Looks interesting :-)

I'll download it and try to get it running after the Christmas holiday.

Merry Christmas :KS

---

### Post by C.S.Cameron on 2012-12-24
If you time how long it takes to fill your pendrive and multiply that by 10000 writes, (reads don't shorten the life), and divide that by the number of hours a day you plan on using the pendrive,

you won't worry much about bricking one.

Even if you do, you can still read from it.

Plus, most pendrives have a long guarantee.

I have never heard of anyone bricking a pendrive, running Linux from it.

---

### Post by rvndmnmt on 2012-12-24
> **C.S.Cameron said:**
> If you time how long it takes to fill your pendrive and multiply that by 10000 writes, (reads don't shorten the life), and divide that by the number of hours a day you plan on using the pendrive,

you won't worry much about bricking one.

Even if you do, you can still read from it.

Plus, most pendrives have a long guarantee.

I have never heard of anyone bricking a pendrive, running Linux from it.

I've burned out a couple :-|  Took a couple years but it does happen.  Don't get me wrong, I usually lose them before that point.  But I can only imagine what an operating system will do.  Like I said, I was a bit drunk when I was inspired by Puppy and the long shutdown times while waiting for the content on ram to be written to the drive.  That could take as long as 9 min.

That aside, I've been running mine up to about 16 hours a day.  I do use it as a primary OS.  It's just easier to carry the computer with me than it is the files.  Might be psychological but I can usually pick up where I left off if I am using the same computer.  Kinda like using the same pen or pencil you took notes with to take the test.

---

