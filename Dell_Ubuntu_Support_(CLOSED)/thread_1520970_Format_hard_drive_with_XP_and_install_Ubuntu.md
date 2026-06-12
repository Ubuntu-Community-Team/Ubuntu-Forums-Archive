---
title: "Format hard drive with XP and install Ubuntu"
date: 2010-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Stormsy on 2010-06-30
Hi there!

I'm not sure if I'm in the right section of the forum to ask this, but here I go;

I have an old Dell Inspiron 2650 laptop with WinXP (SP3, 32-bit) on it, and I would like to completely get rid of XP and put Ubuntu on it so that Ubuntu is the only OS on the hard drive; no dual booting what-so-ever.

How do I go about this?

Also - its an old laptop; only 256 MB RAM, 80 GB HDD, Intel 1.6 GHz (I think).  Runs like cold syrup on XP (for use of a better phrase), I'm hoping it would run faster with Ubuntu on it.  I am thinking of upgrading the RAM to 512 MB to give it a boost...

Many thanks,
Stormsy.

PS: If this thread is in the wrong section of the forum, please move it to an appropriate area.  ^_^

---

### Post by ramnarayan on 2010-06-30
> **Stormsy said:**
> Hi there!


Also - its an old laptop; only 256 MB RAM, 80 GB HDD, Intel 1.6 GHz (I think).  Runs like cold syrup on XP (for use of a better phrase), I'm hoping it would run faster with Ubuntu on it.  I am thinking of upgrading the RAM to 512 MB to give it a boost...

  ^_^

Seems like quite a few people are asking about the same thing

Just pop ubuntu live cd in boot up

then go to system - administration - gparted

once this opens up -just select each partition and delete them one by one.

80 gig is a lot
 
MAKE SURE YOU BACK UP ANY DATA YOU HAVE

**
After that you can 
either close gparted and begin the instal from the desktop icon

or continue in gparted and set you partitions up before hand (i do this)

**
Partitioning
So if you use gparted (or if using the install partitioner - select manual mode)

This will be my partition scheme (assuming that no other OS is being left)

1. 100 MB for /boot  use ext4 file system 
2. 1024 MB (for Swap) 
3. 12 Gig for / (called your root - where you OS is)
4. the remaining can be /home (where your data is)

If you like playing around and experimenting with the latest you could choose to be another partition of 12 GB available for a second OS (linux ) to be dual booted.

I prefer Using gparted to do all this first because it allows you to structure your partitions. You are allowed only 3 primary. Which means if you use the above you actually have 4 or 5

So your 3rd partition has to be extended and under this you can have as many as you want. 

If you want to be flexible keep your /home in a separate primary and arrange the rest as you wish

After this partitioning is done (preferably using gparted) then get on with your install

and then enjoy

ram

---

### Post by mikewhatever on 2010-06-30
The easiest way would be to boot from the cd and, at the partitioning stage, use the entire disk, which will delete everything and install Ubuntu.
That said, with 256MB, I don't know how much luck you'll have with the graphical installation. I have serious doubts it will install and run well. Check the hardware requirements first on ubuntu.com.
Possible Ubuntu based alternatives and derivatives are:
Lubuntu [http://lubuntu.net/](http://lubuntu.net/)
Perpemint [http://peppermintos.com/](http://peppermintos.com/)
There are many more options, but the two above should get you started easily enough.

---

### Post by vanadium on 2010-06-30
256 MM will already work reasonably well. You will feel it when you are launching multiple programs or running a program that is heavy in system resources.

---

### Post by Stormsy on 2010-06-30
Thankyou all for your help.

As I said in my first post I am going to upgrade the RAM to 512 MB.  When I say its old, I mean over 7 yrs old; I think it was purchased 2 yrs before the desktop arrived and the desktop is coming up for 9 yrs now - investigate buying another 2nd HDD in case the main HDD fails!  

The old laptop is not really going to be used for multiple programmes being run all at the same time, more like a 3rd option if someone wants to check their e-mails or surf the web when the desktop or the other laptop is currently in use.

All the data on the HDD is useless anyway - its had so many viral infections that I'm not really sure if its clean or not, it's been a long time since it was connected to the internet.  The best way to make sure is to completely erase anything on it and start fresh with Ubuntu! :D

I shall try and see what happens - in the end its not really worth worrying about it, its old and I didn't consider Ubuntu on it until last night! ^_^

Thanks once again!
Stormsy. :)

---

### Post by julianb on 2010-06-30
Ubuntu will run fine (not super fast, but not too slow either) on 512mb of RAM.

It's best to use a swap partition. PeppermintOS and Lubuntu should also work fine if you want the machine to run faster.

---

