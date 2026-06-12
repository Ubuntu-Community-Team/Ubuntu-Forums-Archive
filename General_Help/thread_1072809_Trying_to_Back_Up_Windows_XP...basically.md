---
title: "Trying to Back Up Windows XP...basically"
date: 2009-02-17
forum: General Help
---

### Post by Tu1J4kXk8NUhMz on 2009-02-17
So I have this thought. I run a MacBook Pro, and use Mac OS X for most everything in conjunction with the tools I've collected in Ubuntu. I also have a Parallels (i.e. Virtualization Software) image running Windows. For various reasons, I want to move my virtual Windows drive back into a physical drive on my MBP.

Plenty of people have had this same issue. However, the solution is either reinstall, or a horrendous 48 step, two-computer-and-an-external-hard-drive solution. I'd like NOT to reinstall, but the latter option is...well, it scares me.

So here's my thought. Seems like Ubuntu would make for a PERFECT solution. I can boot up Ubuntu through my virtual hard drive, create an image and save it out to my external. Then, I could boot up in my physical computer using the same Ubuntu disk to load my Windows image into the appropriate partition. Then comes all the appropriate Windows recovery, etc.

My question is as follows: Is there any Ubuntu software which could backup my Windows partition for transit, then reinstall it elsewhere? Don't worry about the Recovery and such, as I have that part covered.

---

### Post by RedSingularity on 2009-02-17
Do you want to copy the whole Virtual Drive that windows is on?  If so use clonezilla.  I use that to backup my operating systems all the time.  Works great!  You can boot from a CD or a USB drive and you can backup a whole HDD or just a partion of one.  The same program installs the backup you decide to make.

---

### Post by handy on 2009-02-18
You may or may not be familiar with the GPT partitioning scheme that Apple uses?

Personally I find it quite interesting.  There certainly are options that we can take when setting up a dual (or more) boot Mac that uses this Apple scheme, that can be either beneficial or detrimental to our use of the computer with additional OS's in the future.

I contributed a wiki article on installing Arch on a iMac some time ago, some of the information in the first sections up to 1.4 Installing Arch may be of use to you, particularly when it comes to positioning your swap partition.  The information on Apple's partitioning scheme I provide in the wiki is quite comprehensive:

*_[http://wiki.archlinux.org/index.php/IMac_Aluminium](http://wiki.archlinux.org/index.php/IMac_Aluminium)_*

---

### Post by Tu1J4kXk8NUhMz on 2009-02-18
> **Shadow121 said:**
> Do you want to copy the whole Virtual Drive that windows is on?  If so use clonezilla.  I use that to backup my operating systems all the time.  Works great!  You can boot from a CD or a USB drive and you can backup a whole HDD or just a partion of one.  The same program installs the backup you decide to make.

This is quite an interesting idea. I checked up on the website, and it seems like this could be quite a plausible option. Am I able to clone the drive onto an external hard drive? Some of the options out there (in particular, the one suggested by the 48 step pain-in-the-butt method) require extra plug-ins along with networking and other workarounds. That's the whole reason I'm looking at Ubuntu, is that I don't want to worry about workarounds.

---

### Post by RedSingularity on 2009-02-18
Oh yeah you can put it on a External.  Thats how i do it.  I make a backup once a month.  It took me so long to set up my Ubuntu that i dont want to take the chance in loosing it.

---

### Post by RedSingularity on 2009-02-18
And you dont need any extra pluggins.  Just burn the ISO to a cd and boot it.

---

### Post by Tu1J4kXk8NUhMz on 2009-02-21
> **Shadow121 said:**
> Oh yeah you can put it on a External.  Thats how i do it.  I make a backup once a month.  It took me so long to set up my Ubuntu that i dont want to take the chance in loosing it.

*drumming fingers together* Excellent. All is going according to plan. Mwa ha ha!

...er, I mean, awesome! This is quite helpful! If it doesn't work for my Parallels transfer, I'll have to do a little more hunting. But I'm guessing it'll work just fine.

The best part is this thing explains how to make the image smaller, which is just what I need to do!

On a side note, it's good to know I can use this as an effective backup device. Disk Utility on Mac is helpful in backing up Mac drives, but I'm guessing it won't do well backing up anything else...but I need to look into it. Thanks again!

---

### Post by RedSingularity on 2009-02-21
No Problem....Happy to help  :)

---

