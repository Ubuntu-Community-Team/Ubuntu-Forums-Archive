---
title: "help with gparted"
date: 2009-04-13
forum: Desktop Environments
---

### Post by andrea000 on 2009-04-13
A few weeks ago i installed ubuntu 8.04 and windows vista for 
my Mom now (dual boot) she is needing more disk space on ubuntu 
its a 320 GB hard drive only 10 GB on ubuntu how would i go 
about adding more room to ubuntu for her.

---

### Post by inobe on 2009-04-13
there are excellent tips at gparted site.

resizing [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

the site docs [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by andrea000 on 2009-04-13
ok but do i run it from the cd or install it or 
does it matter.

---

### Post by lindsay7 on 2009-04-14
Gparted is in Ubuntu and you can use from there but you have to unmount any drives that you are going to work on and I think it is easier to work from a live Gparted cd. It is handy to have it around anyway so I would just download it from their web site and burn an image to a cd or dvd. Their site also has good documentation on how to use it.

---

### Post by andrea000 on 2009-04-14
could i use the ubuntu cd i am having trouble
bruning the iso to disk?

---

### Post by logos34 on 2009-04-14
> **andrea000 said:**
> could i use the ubuntu cd i am having trouble
bruning the iso to disk?

yes.

live cd desktop>system>admin>partition editor

---

### Post by andrea000 on 2009-04-14
> **logos34 said:**
> yes.

live cd desktop>system>admin>partition editor

Thank you 

I do not know why i can't get the cd 
to burn but i have a ubuntu cd.I was 
not sure this would resize her partition
now i know.wish me luck tomorrow.

---

### Post by e_torano on 2009-04-14
Alternatively, she could just save her files in the Vista partition when working in Ubuntu - that's what I do.

---

### Post by ahbart on 2009-04-14
Be sure to defrag the windows disk before you resize it!

---

### Post by andrea000 on 2009-04-14
> **ahbart said:**
> Be sure to defrag the windows disk before you resize it!

ok but why?

---

### Post by logos34 on 2009-04-14
> **andrea000 said:**
> ok but why?

because if there are fragmented files scattered at the end of the NTFS partition it will block gparted from shrinking the partition enough.  No harm done though. You just need to reboot into windows to fix it. ([This]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=1") used to be the way in XP.  I don't think vista is much diff)

Which reminds me: since it's vista not xp (missed that part), it's generally recommended to resize/shrink windows using vista's own in-built disk tools.  So boot into vista, run defrag and error-checking, then shrink it, reboot to finish the operation and make sure everything is a-ok.  Then use gparted to expand ubuntu into the empty space.

---

### Post by andrea000 on 2009-04-14
Ok i was just curious thank you so much

---

### Post by ahbart on 2009-04-14
Windows file systems have the trouble that files are 'spread over the disk space'. Partition managers find it difficult to resize a fragmented disk. You can find a lot of problem because of this on the internet.

---

### Post by andrea000 on 2009-04-14
ok new problem now my mom no longer want's vista only ubuntu 
so i need to combined the two partition besides doing a new
install is there a way to format the vista side then add it 
to the ubuntu side.

---

### Post by logos34 on 2009-04-14
you can't join or merge the two partitions into one. 

Either format vista side (e.g. as ext3) and add mount point so you can access it from ubuntu.  Or use gparted in ubuntu to delete the vista partition.  Then boot the live cd and use gparted as described above to grow ubuntu to take up the leftover space.

hope that helps

---

### Post by andrea000 on 2009-04-14
That was what i was meaning but did not see anything in 
the doc. about it i may have over looked it but thank
you.

---

### Post by ahbart on 2009-04-15
Another be careful ;) Me again. If you remove the Vista partition, Ubuntu will not be able to boot again. Because Grub can not find the right partitions. You have to reinstall Grub via the live cd.

If you do not have home on a separated partition yet, you could use this Vista partition as home partition. Easiest to do this is with a clean install, but you can find several howto on the internet, like this one: [link](https://help.ubuntu.com/community/Partitioning/Home/Moving)

A separate home partition is easier if you want to reinstall linux anytime in future.

edit: replaced the howto link by another one.

---

### Post by logos34 on 2009-04-15
yes, abhart is right about grub if you decide to delete vista partition.  See link in my signature below for restoring it from live cd.  

Easier still: after you delete vista, you could simply run this in a terminal, which would solve the problem:

> sudo grub-install /dev/sda

That will re-write grub stage1 to MBR of the disk, pointing to / at new Bios address (hd0,0) vs. (hd0,1).  Done.

I wouldn't recommend separate /home for your mom, even though that's how I have mine set up.  Keep it *really* simple. I have a slightly different link in my signature. (doesn't mention the .gvfs file irritation, but it's minor and best ignored).

good luck

---

### Post by andrea000 on 2009-04-15
My mom is no longer want vista so i think i am just going 
to format the hard drive i have done backed up all of the 
data and do a reinstall of ubuntu.I can't grow the ubuntu 
partition for some reason and a freash install of ubuntu
will be faster.I just hate that she/me will have the theme's
to reinstall but still would be faster i thank.

---

### Post by ahbart on 2009-04-15
If you copy your /home/username/.Themes directory you can use it in your new installation I assume.

---

